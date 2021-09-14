---
title: "RefreshConflict element (DataRecordSet_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 373983f7-fc0c-95f6-7665-7ed47de82e5e
description: "Indicates a row in the data recordset linked to a shape that is in conflict after the data recordset is refreshed."
---

# RefreshConflict element (DataRecordSet_Type complexType) (Visio XML)

Indicates a row in the data recordset linked to a shape that is in conflict after the data recordset is refreshed.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RefreshConflict_Type](refreshconflict_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="RefreshConflict" type="RefreshConflict_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Stores, formats, refreshes, and exposes data queried from a database in Microsoft Visio.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|PageID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Page ID of the shape involved in the conflict.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|RowID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The original row ID of the row now in conflict after data was refreshed .  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ShapeID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Shape ID of the shape involved in the conflict.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

