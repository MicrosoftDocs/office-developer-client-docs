---
title: "Relation.Table Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053068
  
localization_priority: Normal
ms.assetid: cc4f64ef-c4e9-1a14-9263-5f8220d89840
description: "Indicates the name of a Relation object's primary table. This should be equal to the Name property setting of a TableDef or QueryDef object (Microsoft Access workspaces only)."
---

# Relation.Table Property (DAO)

Indicates the name of a **[Relation](relation-object-dao.md)** object's primary table. This should be equal to the **[Name](connection-name-property-dao.md)** property setting of a **[TableDef](tabledef-object-dao.md)** or **[QueryDef](querydef-object-dao.md)** object (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **Table**
  
 *expression*  A variable that represents a **Relation** object. 
  
## Remarks

The **Table** property setting is read/write for a new **Relation** object not yet appended to a collection and read-only for an existing **Relation** object in a **[Relations](relations-collection-dao.md)** collection. 
  
Use the **Table** property with the **[ForeignTable](relation-foreigntable-property-dao.md)** property to define a **Relation** object, which represents the relationship between fields in two tables or queries. Set the **Table** property to the **Name** property setting of the primary **TableDef** or **QueryDef** object, and set the **ForeignTable** property to the **Name** property setting of the foreign (referencing) **TableDef** or **QueryDef** object. The **[Attributes](field-attributes-property-dao.md)** property determines the type of relationship between the two objects. 
  
For example, if you had a list of valid part codes (in a field named PartNo) stored in a ValidParts table, you could establish a one-to-many relationship with an OrderItem table such that if a part code were entered into the OrderItem table, it would have to already be in the ValidParts table. If the part code didn't exist in the ValidParts table and you had not set the **Attributes** property of the **Relation** object to **dbRelationDontEnforce**, a trappable error would occur. 
  
In this case, the ValidParts table is the primary table, so the **Table** property of the **Relation** object would be set to ValidParts and the **ForeignTable** property of the **Relation** object would be set to OrderItem. The **Name** and **ForeignName** properties of the **[Field](field-object-dao.md)** object in the **Relation** object's **[Fields](fields-collection-dao.md)** collection would be set to PartNo. 
  
## Example

This example shows how the **Table**, **ForeignTable**, and **ForeignName** properties define the terms of a **Relation** between two tables. 
  
```
Sub ForeignNameX() 
 
 Dim dbsNorthwind As Database 
 Dim relLoop As Relation 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 Debug.Print "Relation" 
 Debug.Print " Table - Field" 
 Debug.Print " Primary (One) "; 
 Debug.Print ".Table - .Fields(0).Name" 
 Debug.Print " Foreign (Many) "; 
 Debug.Print ".ForeignTable - .Fields(0).ForeignName" 
 
 ' Enumerate the Relations collection of the Northwind 
 ' database to report on the property values of 
 ' the Relation objects and their Field objects. 
 For Each relLoop In dbsNorthwind.Relations 
 With relLoop 
 Debug.Print 
 Debug.Print .Name &amp; " Relation" 
 Debug.Print " Table - Field" 
 Debug.Print " Primary (One) "; 
 Debug.Print .Table &amp; " - " &amp; .Fields(0).Name 
 Debug.Print " Foreign (Many) "; 
 Debug.Print .ForeignTable &amp; " - " &amp; _ 
 .Fields(0).ForeignName 
 End With 
 Next relLoop 
 
 dbsNorthwind.Close 
 
End Sub 

```


