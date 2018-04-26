---
title: "Recordset.EditMode Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3cf67f64-c8c3-ad0a-ce00-6f37a3c264ee
description: "Returns a value that indicates the state of editing for the current record."
---

# Recordset.EditMode Property (DAO)

Returns a value that indicates the state of editing for the current record.
  
## Syntax

 *expression*  . **EditMode**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

The return value is a **Long** that indicates the state of editing. The value can be one of the **[EditModeEnum](editmodeenum-enumeration-dao.md)** constants. 
  
The **EditMode** property is useful when an editing process is interrupted, for example, by an error during validation. You can use the value of the **EditMode** property to determine whether you should use the **[Update](recordset-update-method-dao.md)** or **[CancelUpdate](recordset-cancelupdate-method-dao.md)** method. 
  
You can also check to see if the **[LockEdits](recordset-lockedits-property-dao.md)** property setting is **True** and the **EditMode** property setting is **dbEditInProgress** to determine whether the current page is locked. 
  
## Example

This example shows the value of the **EditMode** property under various conditions. The EditModeOutput function is required for this procedure to run. 
  
```
Sub EditModeX() 
 
 Dim dbsNorthwind As Database 
 Dim rstEmployees As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees", _ 
 dbOpenDynaset) 
 
 ' Show the EditMode property under different editing 
 ' states. 
 With rstEmployees 
 EditModeOutput "Before any Edit or AddNew:", .EditMode 
 .Edit 
 EditModeOutput "After Edit:", .EditMode 
 .Update 
 EditModeOutput "After Update:", .EditMode 
 .AddNew 
 EditModeOutput "After AddNew:", .EditMode 
 .CancelUpdate 
 EditModeOutput "After CancelUpdate:", .EditMode 
 .Close 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 
 
Function EditModeOutput(strTemp As String, _ 
 intEditMode As Integer) 
 
 ' Print report based on the value of the EditMode 
 ' property. 
 Debug.Print strTemp 
 Debug.Print " EditMode = "; 
 
 Select Case intEditMode 
 Case dbEditNone 
 Debug.Print "dbEditNone" 
 Case dbEditInProgress 
 Debug.Print "dbEditInProgress" 
 Case dbEditAdd 
 Debug.Print "dbEditAdd" 
 End Select 
 
End Function 

```


