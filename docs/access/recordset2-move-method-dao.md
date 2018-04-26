---
title: "Recordset2.Move Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: df39c05e-c5f8-3b66-fa5f-c91b687c147d
description: "Moves the position of the current record in a Recordset object."
---

# Recordset2.Move Method (DAO)

Moves the position of the current record in a **[Recordset](recordset-object-dao.md)** object. 
  
## Syntax

 *expression*  . **Move**( ** *Rows* **, ** *StartBookmark* ** ) 
  
 *expression*  A variable that represents a **Recordset2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Rows_ <br/> |Required  <br/> |**Long** <br/> |The number of rows the position will move. If rows is greater than 0, the position is moved forward (toward the end of the file). If rows is less than 0, the position is moved backward (toward the beginning of the file).  <br/> |
| _StartBookmark_ <br/> |Optional  <br/> |**Variant** <br/> |A value identifying a bookmark. If you specify startbookmark, the move begins relative to this bookmark. Otherwise, Move begins from the current record.  <br/> |
   
## Remarks

If you use **Move** to position the current record pointer before the first record, the current record pointer moves to the beginning of the file. If the **Recordset** contains no records and its **[BOF](recordset2-bof-property-dao.md)** property is **True**, using this method to move backward causes an error. 
  
If you use **Move** to position the current record pointer after the last record, the current record pointer position moves to the end of the file. If the **Recordset** contains no records and its **[EOF](recordset2-eof-property-dao.md)** property is **True**, then using this method to move forward causes an error. 
  
If either the **BOF** or **EOF** property is **True** and you attempt to use the **Move** method without a valid bookmark, a run-time error occurs. 
  
> [!NOTE]
>  When you use **Move** on a forward-only-type **Recordset** object, the rows argument must be a positive integer and bookmarks aren't allowed. This means you can only move forward. >  To make the first, last, next, or previous record in a **Recordset** the current record, use either the **MoveFirst**, **MoveLast**, **MoveNext**, or **MovePrevious** method. >  Using **Move** with rows equal to 0 is an easy way to retrieve the underlying data for the current record. This is useful if you want to make sure that the current record has the most recent data from the base tables. It will also cancel any pending **[Edit](recordset2-edit-method-dao.md)** or **[AddNew](recordset-addnew-method-dao.md)** calls. 
  
## Example

This example uses the **Move** method to position the record pointer based on user input. 
  
```
Sub MoveX() 
 
   Dim dbsNorthwind As Database 
   Dim rstSuppliers As Recordset2 
   Dim varBookmark As Variant 
   Dim strCommand As String 
   Dim lngMove As Long 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
   Set rstSuppliers = _ 
      dbsNorthwind.OpenRecordset("SELECT CompanyName, " &amp; _ 
      "City, Country FROM Suppliers ORDER BY CompanyName", _ 
      dbOpenDynaset) 
 
   With rstSuppliers 
      ' Populate recordset. 
      .MoveLast 
      .MoveFirst 
 
      Do While True 
         ' Display information about current record and ask  
         ' how many records to move. 
         strCommand = InputBox( _ 
            "Record " &amp; (.AbsolutePosition + 1) &amp; " of " &amp; _ 
            .RecordCount &amp; vbCr &amp; "Company: " &amp; _ 
            !CompanyName &amp; vbCr &amp; "Location: " &amp; !City &amp; _ 
            ", " &amp; !Country &amp; vbCr &amp; vbCr &amp; _ 
            "Enter number of records to Move " &amp; _ 
            "(positive or negative).") 
 
         If strCommand = "" Then Exit Do 
 
         ' Store bookmark in case the Move doesn't work. 
         varBookmark = .Bookmark 
 
         ' Move method requires parameter of data type Long. 
         lngMove = CLng(strCommand) 
         .Move lngMove 
 
         ' Trap for BOF or EOF. 
         If .BOF Then 
            MsgBox "Too far backward! " &amp; _ 
               "Returning to current record." 
            .Bookmark = varBookmark 
         End If 
         If .EOF Then 
            MsgBox "Too far forward! " &amp; _ 
               "Returning to current record." 
            .Bookmark = varBookmark 
         End If 
      Loop 
      .Close 
   End With 
 
   dbsNorthwind.Close 
 
End Sub 

```


