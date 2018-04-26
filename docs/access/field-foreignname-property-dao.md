---
title: "Field.ForeignName Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5f412ab4-173b-9530-eb4f-71ee30bed9e3
description: "Sets or returns a value that specifies the name of the Field object in a foreign table that corresponds to a field in a primary table for a relationship (Microsoft Access workspaces only)."
---

# Field.ForeignName Property (DAO)

Sets or returns a value that specifies the name of the **[Field](field-object-dao.md)** object in a foreign table that corresponds to a field in a primary table for a relationship (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **ForeignName**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

If the **[Relation](relation-object-dao.md)** object isn't appended to the **[Database](database-object-dao.md)**, but the **Field** is appended to the **Relation** object, the **ForeignName** property is read/write. Once the **Relation** object is appended to the database, the **ForeignName** property is read-only. 
  
Only a **Field** object that belongs to the **Fields** collection of a **Relation** object can support the **ForeignName** property. 
  
The **[Name](connection-name-property-dao.md)** and **ForeignName** property settings for a **Field** object specify the names of the corresponding fields in the primary and foreign tables of a relationship. The **[Table](relation-table-property-dao.md)** and **[ForeignTable](relation-foreigntable-property-dao.md)** property settings for a **Relation** object determine the primary and foreign tables of a relationship. 
  
For example, if you had a list of valid part codes (in a field named PartNo) stored in a ValidParts table, you could establish a relationship with an OrderItem table such that if a part code were entered into the OrderItem table, it would have to already exist in the ValidParts table. If the part code didn't exist in the ValidParts table and you had not set the **[Attributes](field-attributes-property-dao.md)** property of the **Relation** object to **dbRelationDontEnforce**, a trappable error would occur. 
  
In this case, the ValidParts table is the foreign table, so the **ForeignTable** property of the **Relation** object would be set to ValidParts and the **Table** property of the **Relation** object would be set to OrderItem. The **Name** and **ForeignName** properties of the **Field** object in the **Relation** object's **Fields** collection would be set to PartNo. 
  
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


