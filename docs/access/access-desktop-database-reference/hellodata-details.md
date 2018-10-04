﻿---
title: HelloData Details
TOCTitle: HelloData Details
ms:assetid: db51e15c-1b5b-c64a-2f84-34dd0e78c6cf
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250105(v=office.15)
ms:contentKeyID: 48548103
ms.date: 09/18/2015
mtps_version: v=office.15
---

# HelloData Details


**Applies to**: Access 2013 | Office 2013

**In this article**  
GetData  
ExamineData  
EditData  
UpdateData  
Form\_Unload  

The HelloData application steps through the basic operations of a typical ADO application: getting, examining, editing, and updating data. When you start the application, click the first button, **Get Data**. This will run the GetData() subroutine.

## GetData

GetData places a valid connection string into a module-level variable, *m\_sConnStr*. For more information about connection strings, see [Creating the Connection String](creating-the-connection-string.md).

Assign an error handler using a Visual Basic **OnError** statement. For more information about error handling in ADO, see [Chapter 6: Error Handling](chapter-6-error-handling.md). A new **Connection** object is created, and the **CursorLocation** property is set to **adUseClient** because the HelloData example creates a *disconnected Recordset*. This means that once the data has been fetched from the data source, the physical connection with the data source is broken, but you can still work with the data that is cached locally in your **Recordset** object.

After the connection has been opened, assign a SQL string to a variable (sSQL). Then instantiate a new **Recordset** object, m\_oRecordset1 . In the next line of code, open the **Recordset** over the existing **Connection**, passing in . In the next line of code, open the **Recordset** over the existing **Connection**, passing in sSQL as the source of the **Recordset**. You assist ADO in making the determination that the SQL string you have passed as the source for the **Recordset** is a textual definition of a command by passing **adCmdText** in the final argument to the **Recordset** **Open** method. This line also sets the **LockType** and **CursorType** associated with the **Recordset**.

The next line of code sets the **MarshalOptions** property equal to **adMarshalModifiedOnly**. **MarshalOptions** indicates which records should be marshaled to the middle tier (or Web server). For more information about marshaling, see the COM documentation. When using **adMarshalModifiedOnly** with a client-side cursor ([CursorLocation](cursorlocation-property-ado.md) = **adUseClient**), only records that have been modified on the client are written back to the middle tier. Setting **MarshalOptions** to **adMarshalModifiedOnly** can improve performance because fewer rows are marshaled.

Next, disconnect the **Recordset** by setting its **ActiveConnection** property equal to **Nothing**. For more information, see [Disconnecting and Reconnecting the Recordset](disconnecting-and-reconnecting-the-recordset.md) in Chapter 5: Updating and Persisting Data.

Close the connection to the data source and destroy the existing **Connection** object, thereby releasing the resources it consumed.

The final step is to set the **Recordset** as the **DataSource** for the Microsoft DataBound Grid Control on the form so that you can easily display the data from the **Recordset** on the form.

Click the second button, **Examine Data**. This runs the ExamineData subroutine.

## ExamineData

ExamineData uses various methods and properties of the **Recordset** object to display information about the data in the **Recordset**. It reports the number of records by using the **RecordCount** property. It loops through the **Recordset** and prints the value of the **AbsolutePosition** property in the display text box on the form. Also while in the loop, the value of the **Bookmark** property for the third record is placed into a variant variable, *vBookmark*, for later use.

The routine navigates directly back to the third record using the bookmark variable that it stored earlier. The routine calls the WalkFields subroutine, which loops through the **Fields** collection of the **Recordset** and displays details about each **Field** in the collection.

Finally, ExamineData uses the **Filter** property of the **Recordset** to screen for only those records with a CategoryId equal to 2. The result of applying this filter is immediately visible in the display grid on the form.

For more information about the functionality shown in the ExamineData subroutine, see [Chapter 3: Examining Data](chapter-3-examining-data.md).

Next, click the third button, **Edit Data**. This will run the EditData subroutine.

## EditData

When the code enters the EditData subroutine, the **Recordset** is still filtered on CategoryId equal to 2, so only those items that meet the filter criteria are visible. It first loops through the **Recordset** and increases the price of each visible item in the **Recordset** by 10 percent. The value of the **Price** field is changed by setting the **Value** property for that field equal to a new, valid amount.

Remember that the **Recordset** is disconnected from the data source. The changes made in EditData are made only to the locally cached copy of the data. For more information, see [Chapter 4: Editing Data](chapter-4-editing-data.md).

The changes will not be made on the data source until you click the fourth button, **Update Data**. This will run the UpdateData subroutine.

## UpdateData

UpdateData first removes the filter that has been applied to the **Recordset**. The code removes and resets as the **DataSource** for the Microsoft Bound DataGrid on the form so that the unfiltered **Recordset** appears in the grid.

The code then checks to see whether you can move backward in the **Recordset** by using the **Supports** method with the **adMovePrevious** argument.

The routine moves to the first record using the **MoveFirst** method and displays the field's original and current values, using the **OriginalValue** and **Value** properties of the **Field** object. These properties, along with the **UnderlyingValue** property (not used here), are discussed in [Chapter 5: Updating and Persisting Data](chapter-5-updating-and-persisting-data.md).

Next, a new **Connection** object is created and used to reestablish a connection to the data source. You reconnect the **Recordset** to the data source by setting the new **Connection** as the **ActiveConnection** for the **Recordset**. To send the updates to the server, the code calls **UpdateBatch** on the **Recordset**.

If the batch update succeeds, a module-level flag variable, , is set to True. This will remind you later to clean up all changes made to the database.

Finally, the code moves back to the first record in the **Recordset** and displays the original and current values. The values are the same after the call to **UpdateBatch**.

For more detailed information about updating data, including what to do when data on the server changes while your **Recordset** is disconnected, see [Chapter 5: Updating and Persisting Data](chapter-5-updating-and-persisting-data.md).

## Form\_Unload

The Form\_Unload subroutine is important for several reasons. First, because this is a sample application, Form\_Unload cleans up the changes made to the database before the application exits. Second, the code shows how a command can be executed directly from an open **Connection** object using the **Execute** method. Finally, it shows an example of executing a non-row–returning query (an UPDATE query) against the data source.

