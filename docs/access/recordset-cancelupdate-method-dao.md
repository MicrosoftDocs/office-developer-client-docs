---
title: "Recordset.CancelUpdate Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053072
  
localization_priority: Normal
ms.assetid: efc4f60b-876f-5e11-37fd-0fbbf225b15b

description: "Cancels any pending updates for a Recordset object."
---

# Recordset.CancelUpdate Method (DAO)

Cancels any pending updates for a **[Recordset](recordset-object-dao.md)** object. 
  
## Syntax

 *expression*  . **CancelUpdate**( ** *UpdateType* ** ) 
  
 *expression*  A variable that represents a **Recordset** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _UpdateType_ <br/> |Optional  <br/> |**Long** <br/> |Set to one of the **[UpdateTypeEnum](updatetypeenum-enumeration-dao.md)** values.  <br/> > [!NOTE]> The  *dbUpdateRegular*  and  *dbUpdateBatch*  values are valid only if batch updating is enabled.           |
   
## Remarks

You can use the **CancelUpdate** method to cancel any pending updates resulting from an **[Edit](recordset-edit-method-dao.md)** or **[AddNew](recordset-addnew-method-dao.md)** operation. For example, if a user invokes the **Edit** or **AddNew** method and hasn't yet invoked the **Update** method, **CancelUpdate** cancels any changes made after **Edit** or **AddNew** was invoked. 
  
Check the **[EditMode](recordset-editmode-property-dao.md)** property of the **Recordset** to determine if there is a pending operation that can be canceled. 
  
> [!NOTE]
> Using the **CancelUpdate** method has the same effect as moving to another record without using the **[Update](recordset-update-method-dao.md)** method, except that the current record doesn't change, and various properties, such as **[BOF](recordset-bof-property-dao.md)** and **[EOF](recordset-eof-property-dao.md)**, aren't updated. 
  
## Example

This example shows how the **CancelUpdate** method is used with the **AddNew** method. 
  
```
Sub CancelUpdateX() 
 
   Dim dbsNorthwind As Database 
   Dim rstEmployees As Recordset 
   Dim intCommand As Integer 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
   Set rstEmployees = dbsNorthwind.OpenRecordset( _ 
      "Employees", dbOpenDynaset) 
 
   With rstEmployees 
      .AddNew 
      !FirstName = "Kimberly" 
      !LastName = "Bowen" 
      intCommand = MsgBox("Add new record for " &amp; _ 
         !FirstName &amp; " " &amp; !LastName &amp; "?", vbYesNo) 
      If intCommand = vbYes Then 
         .Update 
         MsgBox "Record added." 
         ' Delete new record because this is a  
         ' demonstration. 
         .Bookmark = .LastModified 
         .Delete 
      Else 
         .CancelUpdate 
         MsgBox "Record not added." 
      End If 
   End With 
 
   dbsNorthwind.Close 
 
End Sub 

```

This example shows how the **CancelUpdate** method is used with the **Edit** method. 
  
```
Sub CancelUpdateX2() 
 
   Dim dbsNorthwind As Database 
   Dim rstEmployees As Recordset 
   Dim strFirst As String 
   Dim strLast As String 
   Dim intCommand As Integer 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
   Set rstEmployees = dbsNorthwind.OpenRecordset( _ 
      "Employees", dbOpenDynaset) 
 
   With rstEmployees 
      strFirst = !FirstName 
      strLast = !LastName 
      .Edit 
      !FirstName = "Cora" 
      !LastName = "Edmonds" 
      intCommand = MsgBox("Replace current name with " &amp; _ 
         !FirstName &amp; " " &amp; !LastName &amp; "?", vbYesNo) 
      If intCommand = vbYes Then 
         .Update 
         MsgBox "Record modified." 
         ' Restore data because this is a demonstration. 
         .Bookmark = .LastModified 
         .Edit 
         !FirstName = strFirst 
         !LastName = strLast 
         .Update 
      Else 
         .CancelUpdate 
         MsgBox "Record not modified." 
      End If 
      .Close 
   End With 
 
   dbsNorthwind.Close 
 
End Sub 
 
```

