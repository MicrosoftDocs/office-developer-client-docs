---
title: "Relation.Attributes Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: db19d2ad-5965-214c-211d-9a8eb9c3c522
description: "Sets or returns a value that indicates one or more characteristics of a Relation object. Read/write Long ."
---

# Relation.Attributes Property (DAO)

Sets or returns a value that indicates one or more characteristics of a **Relation** object. Read/write **Long**. 
  
## Syntax

 *expression*  . **Attributes**
  
 *expression*  A variable that represents a **Relation** object. 
  
## Remarks

For an object not yet appended to a collection, this property is read/write.
  
## Example

This example displays the **Attributes** property for **Field**, **Relation**, and **TableDef** objects in the Northwind database. 
  
```
Sub AttributesX() 
 
 Dim dbsNorthwind As Database 
 Dim fldLoop As Field 
 Dim relLoop As Relation 
 Dim tdfloop As TableDef 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 
 ' Display the attributes of a TableDef object's 
 ' fields. 
 Debug.Print "Attributes of fields in " &amp; _ 
 .TableDefs(0).Name &amp; " table:" 
 For Each fldLoop In .TableDefs(0).Fields 
 Debug.Print " " &amp; fldLoop.Name &amp; " = " &amp; _ 
 fldLoop.Attributes 
 Next fldLoop 
 
 ' Display the attributes of the Northwind database's 
 ' relations. 
 Debug.Print "Attributes of relations in " &amp; _ 
 .Name &amp; ":" 
 For Each relLoop In .Relations 
 Debug.Print " " &amp; relLoop.Name &amp; " = " &amp; _ 
 relLoop.Attributes 
 Next relLoop 
 
 ' Display the attributes of the Northwind database's 
 ' tables. 
 Debug.Print "Attributes of tables in " &amp; .Name &amp; ":" 
 For Each tdfloop In .TableDefs 
 Debug.Print " " &amp; tdfloop.Name &amp; " = " &amp; _ 
 tdfloop.Attributes 
 Next tdfloop 
 
 .Close 
 End With 
 
End Sub 
 
```


