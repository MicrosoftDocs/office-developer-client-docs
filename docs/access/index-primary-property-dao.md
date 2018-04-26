---
title: "Index.Primary Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052908
  
localization_priority: Normal
ms.assetid: 90eda1cb-cf7f-9682-9b74-81c27a37af16
description: "Sets or returns a value that indicates whether an Index object represents a primary key index for a table (Microsoft Access workspaces only)."
---

# Index.Primary Property (DAO)

Sets or returns a value that indicates whether an **[Index](index-object-dao.md)** object represents a primary key index for a table (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **Primary**
  
 *expression*  A variable that represents an **Index** object. 
  
## Remarks

The **Primary** property setting is read/write for a new **Index** object not yet appended to a collection and read-only for an existing **Index** object in an **[Indexes](indexes-collection-dao.md)** collection. If the **Index** object is appended to the **[TableDef](tabledef-object-dao.md)** object but the **TableDef** object isn't appended to the **[TableDefs](tabledefs-collection-dao.md)** collection, the **Index** property is read/write. 
  
A primary key index consists of one or more fields that uniquely identify all records in a table in a predefined order. Because the index field must be unique, the **[Unique](index-unique-property-dao.md)** property of the **Index** object is set to **True**. If the primary key index consists of more than one field, each field can contain duplicate values, but each combination of values from all the indexed fields must be unique. A primary key index consists of a key for the table and usually contains the same fields as the primary key. 
  
> [!NOTE]
> You don't have to create indexes for tables, but in large, unindexed tables, accessing a specific record can take a long time. The **[Attributes](field-attributes-property-dao.md)** property of each **[Field](field-object-dao.md)** object in the **Index** object determines the order of records and consequently determines the access techniques to use for that index. When you create a new table in your database, it's a good idea to create an index on one or more fields that uniquely identify each record, and then set the **Primary** property of the **Index** object to **True**. 
  
When you set a primary key for a table, the primary key is automatically defined as the primary key index for the table.
  
## Example

This example uses the **Primary** property to designate a new **Index** in a new **TableDef** as the primary **Index** for that table. Note that setting the **Primary** property to **True** automatically sets **Unique** and **Required** properties to **True** as well. 
  
```
Sub PrimaryX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfNew As TableDef 
 Dim idxNew As Index 
 Dim idxLoop As Index 
 Dim fldLoop As Field 
 Dim prpLoop As Property 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 ' Create and append a new TableDef object to the 
 ' TableDefs collection of the Northwind database. 
 Set tdfNew = dbsNorthwind.CreateTableDef("NewTable") 
 tdfNew.Fields.Append tdfNew.CreateField("NumField", _ 
 dbLong, 20) 
 tdfNew.Fields.Append tdfNew.CreateField("TextField", _ 
 dbText, 20) 
 dbsNorthwind.TableDefs.Append tdfNew 
 
 With tdfNew 
 ' Create and append a new Index object to the 
 ' Indexes collection of the new TableDef object. 
 Set idxNew = .CreateIndex("NumIndex") 
 idxNew.Fields.Append idxNew.CreateField("NumField") 
 idxNew.Primary = True 
 .Indexes.Append idxNew 
 Set idxNew = .CreateIndex("TextIndex") 
 idxNew.Fields.Append idxNew.CreateField("TextField") 
 .Indexes.Append idxNew 
 
 Debug.Print .Indexes.Count &amp; " Indexes in " &amp; _ 
 .Name &amp; " TableDef" 
 
 ' Enumerate Indexes collection. 
 For Each idxLoop In .Indexes 
 
 With idxLoop 
 Debug.Print " " &amp; .Name 
 
 ' Enumerate Fields collection of each Index 
 ' object. 
 Debug.Print " Fields" 
 For Each fldLoop In .Fields 
 Debug.Print " " &amp; fldLoop.Name 
 Next fldLoop 
 
 ' Enumerate Properties collection of each 
 ' Index object. 
 Debug.Print " Properties" 
 For Each prpLoop In .Properties 
 Debug.Print " " &amp; prpLoop.Name &amp; _ 
 " = " &amp; IIf(prpLoop = "", "[empty]", _ 
 prpLoop) 
 Next prpLoop 
 End With 
 
 Next idxLoop 
 
 End With 
 
 dbsNorthwind.TableDefs.Delete tdfNew.Name 
 dbsNorthwind.Close 
 
End Sub 

```


