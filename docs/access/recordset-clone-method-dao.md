---
title: "Recordset.Clone Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052909
  
localization_priority: Normal
ms.assetid: 50cbc011-7e72-4dee-488d-96e681618e8e
description: "Creates a duplicate Recordset object that refers to the original Recordset object."
---

# Recordset.Clone Method (DAO)

Creates a duplicate **[Recordset](recordset-object-dao.md)** object that refers to the original **Recordset** object. 
  
## Syntax

 *expression*  . **Clone**
  
 *expression*  A variable that represents a **Recordset** object. 
  
### Return Value

Recordset
  
## Remarks

Use the **Clone** method to create multiple, duplicate **Recordset** objects. Each **Recordset** can have its own current record. Using **Clone** by itself doesn't change the data in the objects or in their underlying structures. When you use the **Clone** method, you can share bookmarks between two or more **Recordset** objects because their bookmarks are interchangeable. 
  
You can use the **Clone** method when you want to perform an operation on a **Recordset** that requires multiple current records. This is faster and more efficient than opening a second **Recordset**. When you create a **Recordset** with the **Clone** method, it initially lacks a current record. To make a record current before you use the **Recordset** clone, you must set the **[Bookmark](recordset-bookmark-property-dao.md)** property or use one of the **[Move](recordset-movefirst-method-dao.md)** methods, one of the **[Find](recordset-findfirst-method-dao.md)** methods, or the **[Seek](recordset-seek-method-dao.md)** method. 
  
Using the **[Close](connection-close-method-dao.md)** method on either the original or duplicate object doesn't affect the other object. For example, using **Close** on the original **Recordset** doesn't close the clone. 
  
> [!NOTE]
>  Closing a clone recordset within a pending transaction will cause an implicit **Rollback** operation. >  When you clone a table-type **Recordset** object in a Microsoft Access workspace, the **[Index](recordset2-index-property-dao.md)** property setting is not cloned on the new copy of the recordset. You must copy the **Index** property setting manually. 
  
## Example

This example uses the **Clone** method to create copies of a **Recordset** and then lets the user position the record pointer of each copy independently. 
  
```
Sub CloneX() 
 
   Dim dbsNorthwind As Database 
   Dim arstProducts(1 To 3) As Recordset 
   Dim intLoop As Integer 
   Dim strMessage As String 
   Dim strFind As String 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
   ' If the following SQL statement will be used often,  
   ' creating a permanent QueryDef will result in better 
   ' performance. 
   Set arstProducts(1) = dbsNorthwind.OpenRecordset( _ 
      "SELECT ProductName FROM Products " &amp; _ 
      "ORDER BY ProductName", dbOpenSnapshot) 
 
   ' Create two clones of the original Recordset. 
   Set arstProducts(2) = arstProducts(1).Clone 
   Set arstProducts(3) = arstProducts(1).Clone 
 
   Do While True 
 
      ' Loop through the array so that on each pass, the  
      ' user is searching a different copy of the same  
      ' Recordset. 
      For intLoop = 1 To 3 
 
         ' Ask for search string while showing where the 
         ' current record pointer is for each Recordset. 
         strMessage = _ 
            "Recordsets from Products table:" &amp; vbCr &amp; _ 
            "  1 - Original - Record pointer at " &amp; _ 
            arstProducts(1)!ProductName &amp; vbCr &amp; _ 
            "  2 - Clone - Record pointer at " &amp; _ 
            arstProducts(2)!ProductName &amp; vbCr &amp; _ 
            "  3 - Clone - Record pointer at " &amp; _ 
            arstProducts(3)!ProductName &amp; vbCr &amp; _ 
            "Enter search string for #" &amp; intLoop &amp; ":" 
         strFind = Trim(InputBox(strMessage)) 
         If strFind = "" Then Exit Do 
 
         ' Find the search string; if there's no match, jump 
         ' to the last record. 
         With arstProducts(intLoop) 
            .FindFirst "ProductName >= '" &amp; strFind &amp; "'" 
            If .NoMatch Then .MoveLast 
         End With 
 
      Next intLoop 
 
   Loop 
 
   arstProducts(1).Close 
   arstProducts(2).Close 
   arstProducts(3).Close 
   dbsNorthwind.Close 
 
End Sub 

```


