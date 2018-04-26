---
title: "Field2.Attributes Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052896
  
localization_priority: Normal
ms.assetid: 08ae9b6b-21e4-9b7e-0852-cfc6639027a7
description: "Sets or returns a value that indicates one or more characteristics of a Field2 object. Read/write Long ."
---

# Field2.Attributes Property (DAO)

Sets or returns a value that indicates one or more characteristics of a **Field2** object. Read/write **Long**. 
  
## Syntax

 *expression*  . **Attributes**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

The value specifies characteristics of the field represented by the **Field2** object and can be a combination of these constants. 
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbAutoIncrField** <br/> |The field value for new records is automatically incremented to a unique Long integer that can't be changed (in a Microsoft Access workspace, supported only for Microsoft Access database engine database tables).  <br/> |
|**dbDescending** <br/> |The field is sorted in descending (Z to A or 100 to 0) order; this option applies only to a **Field2** object in a **Fields** collection of an **Index** object. If you omit this constant, the field is sorted in ascending (A to Z or 0 to 100) order. This is the default value for **Index** and **TableDef** fields (Microsoft Access workspaces only)..  <br/> |
|**dbFixedField** <br/> |The field size is fixed (default for Numeric fields).  <br/> |
|**dbHyperlinkField** <br/> |The field contains hyperlink information (Memo fields only).  <br/> |
|**dbSystemField** <br/> |The field stores replication information for replicas; you can't delete this type of field (Microsoft Access workspaces only).  <br/> |
|**dbUpdatableField** <br/> |The field value can be changed.  <br/> |
|**dbVariableField** <br/> |The field size is variable (Text fields only).  <br/> |
   
For an object not yet appended to a collection, this property is read/write. For an appended **Field2** object, the availability of the **Attributes** property depends on the object that contains the **Fields** collection. 
  
|**If the Field object belongs to an**|**Then Attributes is**|
|:-----|:-----|
|**Index** object  <br/> |Read/write until the **TableDef** object that the **Index** object is appended to is appended to a **Database** object; then the property is read-only.  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   
When you set multiple attributes, you can combine them by summing the appropriate constants. Any invalid values are ignored without producing an error.
  
## Example

This example displays the **Attributes** property for **Field2**, **Relation**, and **TableDef** objects in the Northwind database. 
  
```
Sub AttributesX() 
 
 Dim dbsNorthwind As Database 
 Dim fldLoop As Field2 
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


