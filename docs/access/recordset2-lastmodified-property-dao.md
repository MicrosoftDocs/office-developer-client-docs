---
title: "Recordset2.LastModified Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 1c13cb43-23b5-73b6-af00-a3676cc37cc7
description: "Returns a ookmark indicating the most recently added or changed record."
---

# Recordset2.LastModified Property (DAO)

Returns a ookmark indicating the most recently added or changed record.
  
## Syntax

 *expression*  . **LastModified**
  
 *expression*  A variable that represents a **Recordset2** object. 
  
## Remarks

You can use the **LastModified** property to move to the most recently added or updated record. Use the **LastModified** property with table- and dynaset-type **[Recordset](recordset-object-dao.md)** objects. A record must be added or modified in the **Recordset** object itself in order for the **LastModified** property to have a value. 
  
## Example

This example uses the **LastModified** property to move the current record pointer to both a record that has been modified and a newly created record. 
  
```
Sub LastModifiedX() 
 
 Dim dbsNorthwind As Database 
 Dim rstEmployees As Recordset2 
 Dim strFirst As String 
 Dim strLast As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees", _ 
 dbOpenDynaset) 
 
 With rstEmployees 
 ' Store current data. 
 strFirst = !FirstName 
 strLast = !LastName 
 ' Change data in current record. 
 .Edit 
 !FirstName = "Julie" 
 !LastName = "Warren" 
 .Update 
 ' Move current record pointer to the most recently 
 ' changed or added record. 
 .Bookmark = .LastModified 
 Debug.Print _ 
 "Data in LastModified record after Edit: " &amp; _ 
 !FirstName &amp; " " &amp; !LastName 
 
 ' Restore original data because this is a demonstration. 
 .Edit 
 !FirstName = strFirst 
 !LastName = strLast 
 .Update 
 
 ' Add new record. 
 .AddNew 
 !FirstName = "Roger" 
 !LastName = "Harui" 
 .Update 
 ' Move current record pointer to the most recently 
 ' changed or added record. 
 .Bookmark = .LastModified 
 Debug.Print _ 
 "Data in LastModified record after AddNew: " &amp; _ 
 !FirstName &amp; " " &amp; !LastName 
 
 ' Delete new record because this is a demonstration. 
 .Delete 
 .Close 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 

```

This example uses the **AddNew** method to create a new record with the specified name. The AddName function is required for this procedure to run. 
  
```
Sub AddNewX() 
 
 Dim dbsNorthwind As Database 
 Dim rstEmployees As Recordset2 
 Dim strFirstName As String 
 Dim strLastName As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees", dbOpenDynaset) 
 
 ' Get data from the user. 
 strFirstName = Trim(InputBox( _ 
 "Enter first name:")) 
 strLastName = Trim(InputBox( _ 
 "Enter last name:")) 
 
 ' Proceed only if the user actually entered something 
 ' for both the first and last names. 
 If strFirstName <> "" and strLastName <> "" Then 
 
 ' Call the function that adds the record. 
 AddName rstEmployees, strFirstName, strLastName 
 
 ' Show the newly added data. 
 With rstEmployees 
 Debug.Print "New record: " &amp; !FirstName &amp; _ 
 " " &amp; !LastName 
 ' Delete new record because this is a demonstration. 
 .Delete 
 End With 
 
 Else 
 Debug.Print _ 
 "You must input a string for first and last name!" 
 End If 
 
 rstEmployees.Close 
 dbsNorthwind.Close 
 
End Sub 
 
Function AddName(rstTemp As Recordset, _ 
 strFirst As String, strLast As String) 
 
 ' Adds a new record to a Recordset using the data passed 
 ' by the calling procedure. The new record is then made 
 ' the current record. 
 With rstTemp 
 .AddNew 
 !FirstName = strFirst 
 !LastName = strLast 
 .Update 
 .Bookmark = .LastModified 
 End With 
 
End Function 

```


