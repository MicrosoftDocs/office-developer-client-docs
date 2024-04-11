---
title: "SnapSettings element (DocumentSettings_Type complexType) (Visio XML)"
description: "SnapSettings element (DocumentSettings_Type complexType) (Visio XML) specifies the objects that shapes snap to when snap is active in the window."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 6e86e943-bd29-0a7b-3d6a-d91281f98777
---

# SnapSettings element (DocumentSettings_Type complexType) (Visio XML)

Specifies the objects that shapes snap to when snap is active in the window.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[SnapSettings_Type](snapsettings_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="SnapSettings" type="SnapSettings_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DocumentSettings](documentsettings-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSettings_Type](documentsettings_type-complextypevisio-xml.md) <br/> |Contains elements that specify document settings. |
   
### Child elements

None.
  
### Attributes

None.
  
## Remarks

The value may be a sum of the values in the following table.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Snap to nothing. |
|1  <br/> |Snap to ruler subdivisions. |
|2  <br/> |Snap to grid. |
|4  <br/> |Snap to guides. |
|8  <br/> |Snap to selection handles. |
|16  <br/> |Snap to vertices. |
|32  <br/> |Snap to connection points. |
|256  <br/> |Snap to visible edges of shapes. |
|512  <br/> |Snap to alignment box. |
|1024  <br/> |Snap to shape extensions options. |
|32768  <br/> |Snap disabled. |
|65536  <br/> |Snap to intersections. |
   

