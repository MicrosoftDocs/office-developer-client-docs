---
title: "Fields.Delete Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052868
  
localization_priority: Normal
ms.assetid: a8e249e7-7526-3eff-a5cf-70cab2081970
description: "Deletes a Field from the Fields collection."
---

# Fields.Delete Method (DAO)

Deletes a **[Field](field-object-dao.md)** from the **[Fields](fields-collection-dao.md)** collection. 
  
## Syntax

 *expression*  . **Delete**( ** *Name* ** ) 
  
 *expression*  A variable that represents a **Fields** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |The field to delete.  <br/> |
   
## Remarks

The deletion of a stored object occurs immediately, but you should use the **Refresh** method on any other collections that may be affected by changes to the database structure. 
  
## Example

This example uses either the **Append** method or the **Delete** method to modify the **Fields** collection of a **TableDef**. The AppendDeleteField procedure is required for this procedure to run. 
  
```
Sub AppendX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim fldLoop As Field 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind.TableDefs!Employees 
 
 ' Add three new fields. 
 AppendDeleteField tdfEmployees, "APPEND", _ 
 "E-mail", dbText, 50 
 AppendDeleteField tdfEmployees, "APPEND", _ 
 "Http", dbText, 80 
 AppendDeleteField tdfEmployees, "APPEND", _ 
 "Quota", dbInteger, 5 
 
 Debug.Print "Fields after Append" 
 Debug.Print , "Type", "Size", "Name" 
 
 ' Enumerate the Fields collection to show the new fields. 
 For Each fldLoop In tdfEmployees.Fields 
 Debug.Print , fldLoop.Type, fldLoop.Size, fldLoop.Name 
 Next fldLoop 
 
 ' Delete the newly added fields. 
 AppendDeleteField tdfEmployees, "DELETE", "E-mail" 
 AppendDeleteField tdfEmployees, "DELETE", "Http" 
 AppendDeleteField tdfEmployees, "DELETE", "Quota" 
 
 Debug.Print "Fields after Delete" 
 Debug.Print , "Type", "Size", "Name" 
 
 ' Enumerate the Fields collection to show that the new 
 ' fields have been deleted. 
 For Each fldLoop In tdfEmployees.Fields 
 Debug.Print , fldLoop.Type, fldLoop.Size, fldLoop.Name 
 Next fldLoop 
 
 dbsNorthwind.Close 
 
End Sub 
 
Sub AppendDeleteField(tdfTemp As TableDef, _ 
 strCommand As String, strName As String, _ 
 Optional varType, Optional varSize) 
 
 With tdfTemp 
 
 ' Check first to see if the TableDef object is 
 ' updatable. If it isn't, control is passed back to 
 ' the calling procedure. 
 If .Updatable = False Then 
 MsgBox "TableDef not Updatable! " &amp; _ 
 "Unable to complete task." 
 Exit Sub 
 End If 
 
 ' Depending on the passed data, append or delete a 
 ' field to the Fields collection of the specified 
 ' TableDef object. 
 If strCommand = "APPEND" Then 
 .Fields.Append .CreateField(strName, _ 
 varType, varSize) 
 Else 
 If strCommand = "DELETE" Then .Fields.Delete _ 
 strName 
 End If 
 
 End With 
 
End Sub 

```


