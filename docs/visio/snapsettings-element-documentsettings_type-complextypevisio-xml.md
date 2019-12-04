---
title: "SnapSettings element (DocumentSettings_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6e86e943-bd29-0a7b-3d6a-d91281f98777
description: "Specifies the objects that shapes snap to when snap is active in the window."
---

# SnapSettings element (DocumentSettings_Type complexType) (Visio XML)

Specifies the objects that shapes snap to when snap is active in the window.
  
## Element information

|||
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
|[DocumentSettings](documentsettings-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSettings_Type](documentsettings_type-complextypevisio-xml.md) <br/> |Contains elements that specify document settings.  <br/> |
   
### Child elements

None.
  
### Attributes

None.
  
## Remarks

The value may be a sum of the values in the following table.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Snap to nothing.  <br/> |
|1  <br/> |Snap to ruler subdivisions.  <br/> |
|2  <br/> |Snap to grid.  <br/> |
|4  <br/> |Snap to guides.  <br/> |
|8  <br/> |Snap to selection handles.  <br/> |
|16  <br/> |Snap to vertices.  <br/> |
|32  <br/> |Snap to connection points.  <br/> |
|256  <br/> |Snap to visible edges of shapes.  <br/> |
|512  <br/> |Snap to alignment box.  <br/> |
|1024  <br/> |Snap to shape extensions options.  <br/> |
|32768  <br/> |Snap disabled.  <br/> |
|65536  <br/> |Snap to intersections.  <br/> |
   

