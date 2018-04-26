---
title: "Index.Foreign Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052974
  
localization_priority: Normal
ms.assetid: 81272436-a506-4b72-fd28-2d68e76d6d9b
description: "Returns a value that indicates whether an Index object represents a foreign key in a table (Microsoft Access workspaces only). ."
---

# Index.Foreign Property (DAO)

Returns a value that indicates whether an **[Index](index-object-dao.md)** object represents a foreign key in a table (Microsoft Access workspaces only). . 
  
## Syntax

 *expression*  . **Foreign**
  
 *expression*  A variable that represents an **Index** object. 
  
## Remarks

The return value is a **Boolean** data type that returns **True** if the **Index** object represents a foreign key. 
  
A foreign key consists of one or more fields in a foreign table that uniquely identify all rows in a primary table.
  
The Microsoft Access database engine creates an **Index** object for the foreign table and sets the **Foreign** property when you create a relationship that enforces referential integrity. 
  
## Example

This example shows how the **Foreign** property can indicate which **Index** objects in a **TableDef** are foreign key indexes. Such indexes are created by the Microsoft Access database engine when a **Relation** is created. The default name for the foreign key indexes is the name of the primary table plus the name of the foreign table. The ForeignOutput function is required for this procedure to run. 
  
```
Sub ForeignX() 
 
 Dim dbsNorthwind As Database 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Print report on foreign key indexes from two 
 ' TableDef objects and a QueryDef object. 
 ForeignOutput .TableDefs!Products 
 ForeignOutput .TableDefs!Orders 
 ForeignOutput .TableDefs![Order Details] 
 
 .Close 
 End With 
 
End Sub 
 
Function ForeignOutput(tdfTemp As TableDef) 
 
 Dim idxLoop As Index 
 
 With tdfTemp 
 Debug.Print "Indexes in " &amp; .Name &amp; " TableDef" 
 ' Enumerate the Indexes collection of the specified 
 ' TableDef object. 
 For Each idxLoop In .Indexes 
 Debug.Print " " &amp; idxLoop.Name 
 Debug.Print " Foreign = " &amp; idxLoop.Foreign 
 Next idxLoop 
 End With 
 
End Function 

```


