---
title: Recordset2.Clone Method (DAO)
TOCTitle: Clone Method
ms:assetid: f0d32cb1-03f6-395d-2509-b2139a5fdc68
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff836567(v=office.15)
ms:contentKeyID: 48548614
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset2.Clone Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Creates a duplicate **[Recordset](recordset-object-dao.md)** object that refers to the original **Recordset2** object.

## Syntax

*expression* .Clone

*expression* A variable that represents a **Recordset2** object.

### Return Value

Recordset

## Remarks

Use the **Clone** method to create multiple, duplicate **Recordset** objects. Each recordset can have its own current record. Using **Clone** by itself doesn't change the data in the objects or in their underlying structures. When you use the **Clone** method, you can share bookmarks between two or more **Recordset2** objects because their bookmarks are interchangeable.

You can use the **Clone** method when you want to perform an operation on a recordset that requires multiple current records. This is faster and more efficient than opening a second recordset. When you create a recordset with the **Clone** method, it initially lacks a current record. To make a record current before you use the recordset clone, you must set the **[Bookmark](recordset2-bookmark-property-dao.md)** property or use one of the **[Move](recordset-movefirst-method-dao.md)** methods, one of the **[Find](recordset2-findfirst-method-dao.md)** methods, or the **[Seek](recordset2-seek-method-dao.md)** method.

Using the **[Close](connection-close-method-dao.md)** method on either the original or duplicate object doesn't affect the other object. For example, using **Close** on the original recordset doesn't close the clone.


> [!NOTE]
> <UL>
> <LI>
> <P>Closing a clone recordset within a pending transaction will cause an implicit <STRONG>Rollback</STRONG> operation.</P>
> <LI>
> <P>When you clone a table-type <STRONG>Recordset</STRONG> object in a Microsoft Access workspace, the <STRONG><A href="recordset2-index-property-dao.md">Index</A></STRONG> property setting is not cloned on the new copy of the recordset. You must copy the <STRONG>Index</STRONG> property setting manually.</P></LI></UL>



## Example

This example uses the **Clone** method to create copies of a recordset and then lets the user position the record pointer of each copy independently.

    Sub CloneX() 
     
       Dim dbsNorthwind As Database 
       Dim arstProducts(1 To 3) As Recordset2 
       Dim intLoop As Integer 
       Dim strMessage As String 
       Dim strFind As String 
     
       Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
     
       ' If the following SQL statement will be used often,  
       ' creating a permanent QueryDef will result in better 
       ' performance. 
       Set arstProducts(1) = dbsNorthwind.OpenRecordset( _ 
          "SELECT ProductName FROM Products " & _ 
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
                "Recordsets from Products table:" & vbCr & _ 
                "  1 - Original - Record pointer at " & _ 
                arstProducts(1)!ProductName & vbCr & _ 
                "  2 - Clone - Record pointer at " & _ 
                arstProducts(2)!ProductName & vbCr & _ 
                "  3 - Clone - Record pointer at " & _ 
                arstProducts(3)!ProductName & vbCr & _ 
                "Enter search string for #" & intLoop & ":" 
             strFind = Trim(InputBox(strMessage)) 
             If strFind = "" Then Exit Do 
     
             ' Find the search string; if there's no match, jump 
             ' to the last record. 
             With arstProducts(intLoop) 
                .FindFirst "ProductName >= '" & strFind & "'" 
                If .NoMatch Then .MoveLast 
             End With 
     
          Next intLoop 
     
       Loop 
     
       arstProducts(1).Close 
       arstProducts(2).Close 
       arstProducts(3).Close 
       dbsNorthwind.Close 
     
    End Sub

