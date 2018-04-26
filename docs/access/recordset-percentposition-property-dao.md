---
title: "Recordset.PercentPosition Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: aebbda44-ed72-7a6c-0cd5-28c8997d4d96
description: "Sets or returns a value indicating the approximate location of the current record in the Recordset object based on a percentage of the records in the Recordset ."
---

# Recordset.PercentPosition Property (DAO)

Sets or returns a value indicating the approximate location of the current record in the **[Recordset](recordset-object-dao.md)** object based on a percentage of the records in the **Recordset**. 
  
## Syntax

 *expression*  . **PercentPosition**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

To indicate or change the approximate position of the current record in a **Recordset** object, you can check or set the **PercentPosition** property. When working with a dynaset- or snapshot-type **Recordset** object opened directly from a base table, first populate the **Recordset** object by moving to the last record before you set or check the **PercentPosition** property. If you use the **PercentPosition** property before fully populating the **Recordset** object, the amount of movement is relative to the number of records accessed as indicated by the **[RecordCount](recordset-recordcount-property-dao.md)** property setting. You can move to the last record by using the **[MoveLast](recordset-movelast-method-dao.md)** method. 
  
> [!NOTE]
> Using the **PercentPosition** property to move the current record to a specific record in a **Recordset** object isn't recommended?the **[Bookmark](recordset-bookmark-property-dao.md)** property is better suited for this task. 
  
Once you set the **PercentPosition** property to a value, the record at the approximate position corresponding to that value becomes current, and the **PercentPosition** property is reset to a value that reflects the approximate position of the current record. For example, if your **Recordset** object contains only five records, and you set its **PercentPosition** property value to 77, the value returned from the **PercentPosition** property may be 80, not 77. 
  
The **PercentPosition** property applies to all types of **Recordset** objects except for forward-only-type **Recordset** objects or **Recordset** objects opened from pass-through queries against remote databases. 
  
You can use the **PercentPosition** property with a scroll bar on a form or text box to indicate the location of the current record in a **Recordset** object. 
  
## Example

This example uses the **PercentPosition** property to show the position of the current record pointer relative to the beginning of the **Recordset**. 
  
```
Sub PercentPositionX() 
 
 Dim dbsNorthwind As Database 
 Dim rstProducts As Recordset 
 Dim strFind As String 
 Dim strMessage As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 ' PercentPosition only works with dynasets or snapshots. 
 Set rstProducts = dbsNorthwind.OpenRecordset( _ 
 "SELECT ProductName FROM Products " &amp; _ 
 "ORDER BY ProductName", dbOpenSnapshot) 
 
 With rstProducts 
 ' Populate the Recordset. 
 .MoveLast 
 .MoveFirst 
 
 Do While True 
 ' Show current record information and ask user 
 ' for input. 
 strMessage = "Product: " &amp; !ProductName &amp; vbCr &amp; _ 
 "The record pointer is " &amp; _ 
 Format(.PercentPosition, "##0.0") &amp; _ 
 "% from the " &amp; vbCr &amp; _ 
 "beginning of the Recordset." &amp; vbCr &amp; _ 
 "Please enter a character search string " &amp; _ 
 "for a product name." 
 strFind = Trim(InputBox(strMessage)) 
 If strFind = "" Then Exit Do 
 
 ' Try to find a record matching the search string. 
 .FindFirst "ProductName >= '" &amp; strFind &amp; "'" 
 If .NoMatch Then .MoveLast 
 Loop 
 
 .Close 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 

```


