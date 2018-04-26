---
title: "Field.Size Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052878
  
localization_priority: Normal
ms.assetid: 15e25201-87b6-f62f-ff18-259414a47891
description: "Sets or returns a value that indicates the maximum size, in bytes, of a Field object."
---

# Field.Size Property (DAO)

Sets or returns a value that indicates the maximum size, in bytes, of a **[Field](field-object-dao.md)** object. 
  
## Syntax

 *expression*  . **Size**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

For an object not yet appended to the **[Fields](fields-collection-dao.md)** collection, this property is read/write. 
  
For fields (other than Memo type fields) that contain character data, the **Size** property indicates the maximum number of characters that the field can hold. For numeric fields, the **Size** property indicates how many bytes of storage are required. 
  
Use of the **Size** property depends on the object that contains the **Fields** collection to which the **Field** object is appended, as shown in the following table. 
  
|**Object appended to**|**Usage**|
|:-----|:-----|
|**Index** <br/> |Not supported  <br/> |
|**QueryDef** <br/> |Read-only  <br/> |
|**Recordset** <br/> |Read-only  <br/> |
|**Relation** <br/> |Not supported  <br/> |
|**TableDef** <br/> |Read-only  <br/> |
   
When you create a **Field** object with a data type other than Text, the **[Type](field-type-property-dao.md)** property setting automatically determines the **Size** property setting; you don't need to set it. For a **Field** object with the Text data type, however, you can set **Size** to any integer up to the maximum text size (255 for Microsoft Access databases). If you do not set the size, the field will be as large as the database allows. 
  
For Long Binary and Memo **Field** objects, **Size** is always set to 0. Use the **[FieldSize](field-fieldsize-property-dao.md)** property of the **Field** object to determine the size of the data in a specific record. The maximum size of a Long Binary or Memo field is limited only by your system resources or the maximum size that the database allows. 
  
## Example

This example demonstrates the **Size** property by enumerating the names and sizes of the **Field** objects in the Employees table. 
  
```
Sub SizeX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim fldNew As Field 
 Dim fldLoop As Field 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind.TableDefs!Employees 
 
 With tdfEmployees 
 
 ' Create and append a new Field object to the 
 ' Employees table. 
 Set fldNew = .CreateField("FaxPhone") 
 fldNew.Type = dbText 
 fldNew.Size = 20 
 .Fields.Append fldNew 
 
 Debug.Print "TableDef: " &amp; .Name 
 Debug.Print " Field.Name - Field.Type - Field.Size" 
 
 ' Enumerate Fields collection; print field names, 
 ' types, and sizes. 
 For Each fldLoop In .Fields 
 Debug.Print " " &amp; fldLoop.Name &amp; " - " &amp; _ 
 fldLoop.Type &amp; " - " &amp; fldLoop.Size 
 Next fldLoop 
 
 ' Delete new field because this is a demonstration. 
 .Fields.Delete fldNew.Name 
 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 

```


