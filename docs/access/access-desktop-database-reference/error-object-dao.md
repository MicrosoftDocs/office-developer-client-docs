---
title: Error Object (DAO)
TOCTitle: Error Object
ms:assetid: e2608bc9-bece-9b47-4562-7a2689601f75
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff835711(v=office.15)
ms:contentKeyID: 48548289
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Error Object (DAO)


_**Applies to:** Access 2013 | Office 2013_

**Error** object contains details about data access errors, each of which pertains to a single operation involving DAO.

## Remarks

Any operation involving DAO can generate one or more errors. For example, a call to an ODBC server might result in an error from the database server, an error from ODBC, and a DAO error. As each such error occurs, an **Error** object is placed in the **Errors** collection of the **DBEngine** object. A single event can therefore result in several **Error** objects appearing in the **Errors** collection.

When a subsequent DAO operation generates an error, the **Errors** collection is cleared, and one or more new **Error** objects are placed in the **Errors** collection. DAO operations that don't generate an error have no effect on the **Errors** collection.

The set of **Error** objects in the **Errors** collection describes one error. The first **Error** object is the lowest level error (the originating error), the second the next higher level error, and so forth. For example, if an ODBC error occurs while trying to open a **[Recordset](recordset-object-dao.md)** object, the first **Error** object— **Errors**(0)— contains the lowest level ODBC error; subsequent errors contain the ODBC errors returned by the various layers of ODBC. In this case, the ODBC driver manager, and possibly the driver itself, return separate **Error** objects. The last **Error** object— **Errors.Count-**1— contains the DAO error indicating that the object couldn't be opened.

Enumerating the specific errors in the **Errors** collection enables your error-handling routines to more precisely determine the cause and origin of an error, and take appropriate steps to recover. You can read the **Error** object's properties to obtain specific details about each error, including:

  - The **[Description](error-description-property-dao.md)** property, which contains the text of the error alert that will be displayed on the screen if the error is not trapped.

  - The **[Number](error-number-property-dao.md)** property, which contains the Long integer value of the error constant.

  - The **[Source](error-source-property-dao.md)** property, which identifies the object that raised the error. This is particularly useful when you have several **Error** objects in the **Errors** collection following a request to an ODBC data source.

  - The **HelpFile** and **HelpContext** properties, which indicate the appropriate Microsoft Windows Help file and Help topic, respectively, (if any exist) for the error.
    

    > [!NOTE]
    > <P>When programming in Microsoft Visual Basic for Applications (VBA), if you use the <STRONG>New</STRONG> keyword to create an object that subsequently causes an error before that object has been appended to a collection, the <STRONG>DBEngine</STRONG> object's <STRONG>Errors</STRONG> collection won't contain an entry for that object's error, because the new object is not associated with the <STRONG>DBEngine</STRONG> object. However, the error information is available in the VBA <STRONG>Err</STRONG> object. Your VBA error-handling code should examine the <STRONG>Errors</STRONG> collection whenever you anticipate a data access error. If you are writing a centralized error handler, test the VBA <STRONG>Err</STRONG> object to determine if the error information in the <STRONG>Errors</STRONG> collection is valid. If the <STRONG>Number</STRONG> property of the last element of the <STRONG>Errors</STRONG> collection (DBEngine.Errors.Count - 1) and the value of the <STRONG>Err</STRONG> object match, you can then use a series of <STRONG>Select Case</STRONG> statements to identify the particular DAO error or errors that occurred. If they do not match, use the <STRONG><A href="errors-refresh-method-dao.md">Refresh</A></STRONG> method on the <STRONG>Errors</STRONG> collection.</P>



## Example

This example forces an error, traps it, and displays the **Description**, **Number**, **Source**, **HelpContext**, and **HelpFile** properties of the resulting **Error** object.

``` 
Sub DescriptionX() 
 
   Dim dbsTest As Database 
 
   On Error GoTo ErrorHandler 
 
   ' Intentionally trigger an error. 
   Set dbsTest = OpenDatabase("NoDatabase") 
 
   Exit Sub 
 
ErrorHandler: 
   Dim strError As String 
   Dim errLoop As Error 
 
   ' Enumerate Errors collection and display properties of  
   ' each Error object. 
   For Each errLoop In Errors 
      With errLoop 
         strError = _ 
            "Error #" & .Number & vbCr 
         strError = strError & _ 
            "  " & .Description & vbCr 
         strError = strError & _ 
            "  (Source: " & .Source & ")" & vbCr 
         strError = strError & _ 
            "Press F1 to see topic " & .HelpContext & vbCr 
         strError = strError & _ 
            "  in the file " & .HelpFile & "." 
      End With 
      MsgBox strError 
   Next 
 
   Resume Next 
 
End Sub 
 
```

