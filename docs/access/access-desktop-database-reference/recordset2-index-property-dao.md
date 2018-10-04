---
title: Recordset2.Index Property (DAO)
TOCTitle: Index Property
ms:assetid: 614bdf53-aca3-25ef-a23c-50095b345d20
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff194872(v=office.15)
ms:contentKeyID: 48545209
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset2.Index Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Sets or returns a value that indicates the name of the current **[Index](index-object-dao.md)** object in a table-type **[Recordset](recordset-object-dao.md)** object (Microsoft Access workspaces only).

## Syntax

*expression* .Index

*expression* A variable that represents a **Recordset2** object.

## Remarks

Records in base tables aren't stored in any particular order. Setting the **Index** property changes the order of records returned from the database; it doesn't affect the order in which the records are stored.

The specified **Index** object must already be defined. If you set the **Index** property to an **Index** object that doesn't exist or if the **Index** property isn't set when you use the **[Seek](recordset2-seek-method-dao.md)** method, a trappable error occurs.

Examine the **Indexes** collection of a **TableDef** object to determine what **Index** objects are available to table-type **Recordset** objects created from that **TableDef** object.

You can create a new index for the table by creating a new **Index** object, setting its properties, appending it to the **Indexes** collection of the underlying **TableDef** object, and then reopening the **Recordset** object.

Records returned from a table-type **Recordset** object can be ordered only by the indexes defined for the underlying **TableDef** object. To sort records in some other order, you can open a dynaset–, snapshot–, or forward–only–type **Recordset** object by using an SQL statement with an ORDER BY clause.


> [!NOTE]
> <UL>
> <LI>
> <P>You don't have to create indexes for tables. With large, unindexed tables, accessing a specific record or creating a <STRONG>Recordset</STRONG> object can take a long time. On the other hand, creating too many indexes slows down update, append, and delete operations because all indexes are automatically updated.</P>
> <LI>
> <P>Records read from tables without indexes are returned in no particular sequence.</P>
> <LI>
> <P>The <STRONG><A href="field-attributes-property-dao.md">Attributes</A></STRONG> property of each <STRONG><A href="field-object-dao.md">Field</A></STRONG> object in the <STRONG>Index</STRONG> object determines the order of records and consequently determines the access techniques to use for that index.</P>
> <LI>
> <P>A unique index helps optimize finding records.</P>
> <LI>
> <P>Indexes don't affect the physical order of a base tableindexes affect only how the records are accessed by the table-type <STRONG>Recordset</STRONG> object when a particular index is chosen or when <STRONG>Recordset</STRONG> is opened.</P></LI></UL>



## Example

This example uses the **Index** property to set different record orders for a table-type **Recordset**.

    Sub IndexPropertyX() 
     
       Dim dbsNorthwind As Database 
       Dim tdfEmployees As TableDef 
       Dim rstEmployees As Recordset2 
       Dim idxLoop As Index 
     
       Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
       Set rstEmployees = _ 
          dbsNorthwind.OpenRecordset("Employees") 
       Set tdfEmployees = dbsNorthwind.TableDefs!Employees 
     
       With rstEmployees 
     
          ' Enumerate Indexes collection of Employees table. 
          For Each idxLoop In tdfEmployees.Indexes 
             .Index = idxLoop.Name 
             Debug.Print "Index = " & .Index 
             Debug.Print "  EmployeeID - PostalCode - Name" 
             .MoveFirst 
     
             ' Enumerate Recordset to show the order of records. 
             Do While Not .EOF 
                Debug.Print "    " & !EmployeeID & " - " & _ 
                   !PostalCode & " - " & !FirstName & " " & _ 
                   !LastName 
                .MoveNext 
             Loop 
     
          Next idxLoop 
     
          .Close 
       End With 
     
       dbsNorthwind.Close 
     
    End Sub 

This example demonstrates the **Seek** method by allowing the user to search for a product based on an ID number.

    Sub SeekX() 
     
       Dim dbsNorthwind As Database 
       Dim rstProducts As Recordset2 
       Dim intFirst As Integer 
       Dim intLast As Integer 
       Dim strMessage As String 
       Dim strSeek As String 
       Dim varBookmark As Variant 
     
       Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
       ' You must open a table-type Recordset to use an index,  
       ' and hence the Seek method. 
       Set rstProducts = _ 
          dbsNorthwind.OpenRecordset("Products", dbOpenTable) 
     
       With rstProducts 
          ' Set the index. 
          .Index = "PrimaryKey" 
     
          ' Get the lowest and highest product IDs. 
          .MoveLast 
          intLast = !ProductID 
          .MoveFirst 
          intFirst = !ProductID 
     
          Do While True 
             ' Display current record information and ask user  
             ' for ID number. 
             strMessage = "Product ID: " & !ProductID & vbCr & _ 
                "Name: " & !ProductName & vbCr & vbCr & _ 
                "Enter a product ID between " & intFirst & _ 
                " and " & intLast & "." 
             strSeek = InputBox(strMessage) 
     
             If strSeek = "" Then Exit Do 
     
             ' Store current bookmark in case the Seek fails. 
             varBookmark = .Bookmark 
     
             .Seek "=", Val(strSeek) 
     
             ' Return to the current record if the Seek fails. 
             If .NoMatch Then 
                MsgBox "ID not found!" 
                .Bookmark = varBookmark 
             End If 
          Loop 
     
          .Close 
       End With 
     
       dbsNorthwind.Close 
     
    End Sub

