---
title: "Field2.OrdinalPosition Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052899
  
localization_priority: Normal
ms.assetid: 55d89611-ad07-990d-fc33-f81d59472430
description: "Sets or returns the relative position of a Field2 object within a Fields collection. ."
---

# Field2.OrdinalPosition Property (DAO)

Sets or returns the relative position of a **Field2** object within a **[Fields](fields-collection-dao.md)** collection. . 
  
## Syntax

 *expression*  . **OrdinalPosition**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

For an object not yet appended to the **Fields** collection, this property is read/write. 
  
 The default is 0. 
  
The availability of the **OrdinalPosition** property depends on the object that contains the **Fields** collection, as shown in the following table. 
  
|**If the Fields collection belongs to a**|**Then OrdinalPosition is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   
Generally, the ordinal position of an object that you append to a collection depends on the order in which you append the object. The first appended object is in the first position (0), the second appended object is in the second position (1), and so on. The last appended object is in ordinal position  _count_ - 1, where  _count_ is the number of objects in the collection as specified by the **[Count](containers-count-property-dao.md)** property setting. 
  
You can use the **OrdinalPosition** property to specify an ordinal position for new **Field2** objects that differs from the order in which you append those objects to a collection. This enables you to specify a field order for your tables, queries, and recordsets when you use them in an application. For example, the order in which fields are returned in a  `SELECT *` query is determined by the current **OrdinalPosition** property values. 
  
You can permanently reset the order in which fields are returned in recordsets by setting the **OrdinalPosition** property to any positive integer. 
  
Two or more **Field2** objects in the same collection can have the same **OrdinalPosition** property value, in which case they will be ordered alphabetically. For example, if you have a field named Age set to 4 and you set a second field named Weight to 4, Weight is returned after Age. 
  
You can specify a number that is greater than the number of fields minus 1. The field will be returned in an order relative to the largest number. For example, if you set a field's **OrdinalPosition** property to 20 (and there are only 5 fields) and you've set the **OrdinalPosition** property for two other fields to 10 and 30, respectively, the field set to 20 is returned between the fields set to 10 and 30. 
  
> [!NOTE]
> Even if the **Fields** collection of a **[TableDef](tabledef-object-dao.md)** has not been refreshed, the field order in a **[Recordset](recordset-object-dao.md)** opened from the **TableDef** will reflect the **OrdinalPosition** data of the **TableDef** object. A table-type **Recordset** will have the same **OrdinalPosition** data as the underlying table, but any other type of **Recordset** will have new **OrdinalPosition** data (starting with 0) that follow the order determined by the **OrdinalPosition** data of the **TableDef**. 
  
## Example

This example changes the **OrdinalPosition** property values in the Employees **TableDef** in order to control the **Field2** order in a resulting **Recordset**. By setting the **OrdinalPosition** of all the **Fields** to 1, any resulting **Recordset** will order the **Fields** alphabetically. Note that the **OrdinalPosition** values in the **Recordset** don't match the values in the **TableDef**, but simply reflect the end result of the **TableDef** changes. 
  
```
Sub OrdinalPositionX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim aintPosition() As Integer 
 Dim astrFieldName() As String 
 Dim intTemp As Integer 
 Dim fldTemp As Field2 
 Dim rstEmployees As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind.TableDefs("Employees") 
 
 With tdfEmployees 
 ' Display and store original OrdinalPosition data. 
 Debug.Print _ 
 "Original OrdinalPosition data in TableDef." 
 ReDim aintPosition(0 To .Fields.Count - 1) As Integer 
 ReDim astrFieldName(0 To .Fields.Count - 1) As String 
 For intTemp = 0 To .Fields.Count - 1 
 aintPosition(intTemp) = _ 
 .Fields(intTemp).OrdinalPosition 
 astrFieldName(intTemp) = .Fields(intTemp).Name 
 Debug.Print , aintPosition(intTemp), _ 
 astrFieldName(intTemp) 
 Next intTemp 
 
 ' Change OrdinalPosition data. 
 For Each fldTemp In .Fields 
 fldTemp.OrdinalPosition = 1 
 Next fldTemp 
 
 ' Open new Recordset object to show how the 
 ' OrdinalPosition data has affected the record order. 
 Debug.Print _ 
 "OrdinalPosition data from resulting Recordset." 
 Set rstEmployees = dbsNorthwind.OpenRecordset( _ 
 "SELECT * FROM Employees") 
 For Each fldTemp In rstEmployees.Fields 
 Debug.Print , fldTemp.OrdinalPosition, fldTemp.Name 
 Next fldTemp 
 rstEmployees.Close 
 
 ' Restore original OrdinalPosition data because this is 
 ' a demonstration. 
 For intTemp = 0 To .Fields.Count - 1 
 .Fields(astrFieldName(intTemp)).OrdinalPosition = _ 
 aintPosition(intTemp) 
 Next intTemp 
 
 End With 
 
 dbsNorthwind.Close 
 
End Sub 

```


