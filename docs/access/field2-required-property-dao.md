---
title: "Field2.Required Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 7d14dfd7-a50d-6044-469e-1511c74c148d
description: "Sets or returns a value that indicates whether a Field2 object requires a non-Null value."
---

# Field2.Required Property (DAO)

Sets or returns a value that indicates whether a **Field2** object requires a non-Null value. 
  
## Syntax

 *expression*  . **Required**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

For a **Field2** not yet appended to the **Fields** collection, this property is read/write. 
  
The availability of the **Required** property depends on the object that contains the **[Fields](fields-collection-dao.md)** collection, as shown in the following table. 
  
|**If the Fields collection belongs to a**|**Then Required is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   
You can use the **Required** property along with the **AllowZeroLength**, **ValidateOnSet**, or **ValidationRule** property to determine the validity of the **Value** property setting for that **Field2** object. If the **Required** property is set to **False**, the field can contain **null** values as well as values that meet the conditions specified by the **AllowZeroLength** and **ValidationRule** property settings. 
  
> [!NOTE]
> When you can set this property for either an **Index** object or a **Field2** object, set it for the **Field2** object. The validity of the property setting for a **Field2** object is checked before that of an **Index** object. 
  
## Example

This example uses the **Required** property to report which fields in three different tables must contain data in order for a new record to be added. The RequiredOutput procedure is required for this procedure to run. 
  
```
Sub RequiredX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfloop As TableDef 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Show which fields are required in the Fields 
 ' collections of three different TableDef objects. 
 RequiredOutput .TableDefs("Categories") 
 RequiredOutput .TableDefs("Customers") 
 RequiredOutput .TableDefs("Employees") 
 .Close 
 End With 
 
End Sub 
 
Sub RequiredOutput(tdfTemp As TableDef) 
 
 Dim fldLoop As Field2 
 
 ' Enumerate Fields collection of the specified TableDef 
 ' and show the Required property. 
 Debug.Print "Fields in " &amp; tdfTemp.Name &amp; ":" 
 For Each fldLoop In tdfTemp.Fields 
 Debug.Print , fldLoop.Name &amp; ", Required = " &amp; _ 
 fldLoop.Required 
 Next fldLoop 
 
End Sub 
 
```


