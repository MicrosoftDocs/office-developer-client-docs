---
title: "Field.Required Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2f1dbdeb-a37a-59b2-fdc2-f16c7ae1a575
description: "Sets or returns a value that indicates whether a Field object requires a non-Null value."
---

# Field.Required Property (DAO)

Sets or returns a value that indicates whether a **[Field](field-object-dao.md)** object requires a non-Null value. 
  
## Syntax

 *expression*  . **Required**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

For a **Field** not yet appended to the **Fields** collection, this property is read/write. 
  
The availability of the **Required** property depends on the object that contains the [Fields](fields-collection-dao.md) collection, as shown in the following table. 
  
|**If the Fields collection belongs to a**|**Then Required is**|
|:-----|:-----|
|**Index** object  <br/> |Not supported  <br/> |
|**QueryDef** object  <br/> |Read-only  <br/> |
|**Recordset** object  <br/> |Read-only  <br/> |
|**Relation** object  <br/> |Not supported  <br/> |
|**TableDef** object  <br/> |Read/write  <br/> |
   
You can use the **Required** property along with the **[AllowZeroLength](field-allowzerolength-property-dao.md)**, **[ValidateOnSet](field-validateonset-property-dao.md)**, or **[ValidationRule](field-validationrule-property-dao.md)** property to determine the validity of the **[Value](field-value-property-dao.md)** property setting for that **Field** object. If the **Required** property is set to **False**, the field can contain **null** values as well as values that meet the conditions specified by the **AllowZeroLength** and **ValidationRule** property settings. 
  
> [!NOTE]
> When you can set this property for either an **Index** object or a **Field** object, set it for the **Field** object. The validity of the property setting for a **Field** object is checked before that of an **Index** object. 
  
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
 
 Dim fldLoop As Field 
 
 ' Enumerate Fields collection of the specified TableDef 
 ' and show the Required property. 
 Debug.Print "Fields in " &amp; tdfTemp.Name &amp; ":" 
 For Each fldLoop In tdfTemp.Fields 
 Debug.Print , fldLoop.Name &amp; ", Required = " &amp; _ 
 fldLoop.Required 
 Next fldLoop 
 
End Sub 
 
```


