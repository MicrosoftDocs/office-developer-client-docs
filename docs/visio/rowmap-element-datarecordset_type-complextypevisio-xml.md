---
title: "RowMap element (DataRecordSet_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: f90dc76b-7f0b-dead-38c0-97062a7b76a6
description: "Maps a data-recordset row to a shape."
---

# RowMap element (DataRecordSet_Type complexType) ('Visio XML')

Maps a data-recordset row to a shape.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RowMap_Type](rowmap_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="RowMap" type="RowMap_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

****

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Stores, formats, refreshes, and exposes data queried from a database in Microsoft Visio.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|PageID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Page ID of the shape linked to data in the data-recordset row identified by **RowID**.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|RowID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Row ID of the row, unique within the data recordset.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ShapeID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Shape ID of the shape linked to data in the data-recordset row identified by **RowID**.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

