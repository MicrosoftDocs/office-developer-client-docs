---
title: "SnapExtensions element (DocumentSettings_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: d55b6676-125f-7cf1-509d-21dee548f5a1
description: "Specifies whether a specific snap extension setting is enabled or disabled for the active window."
---

# SnapExtensions element (DocumentSettings_Type complexType) (Visio XML)

Specifies whether a specific snap extension setting is enabled or disabled for the active window. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[SnapExtensions_Type](snapextensions_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
<xs:element name="SnapExtensions" type="SnapExtensions_Type" minOccurs="0" maxOccurs="1" >
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

The value of the **SnapExtensions** element can be a sum of the values in the following table. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Snap to nothing.  <br/> |
|1  <br/> |Snap to alignment box extension.  <br/> |
|2  <br/> |Snap to center axis extension.  <br/> |
|4  <br/> |Snap to curve tangent extension.  <br/> |
|8  <br/> |Snap to endpoint extension.  <br/> |
|16  <br/> |Snap to midpoint extension.  <br/> |
|32  <br/> |Snap to linear extension.  <br/> |
|64  <br/> |Snap to curve extension.  <br/> |
|128  <br/> |Snap to endpoint perpendicular extension.  <br/> |
|256  <br/> |Snap to midpoint perpendicular extension.  <br/> |
|512  <br/> |Snap to endpoint horizontal extension.  <br/> |
|1024  <br/> |Snap to endpoint vertical extension.  <br/> |
|2048  <br/> |Snap to ellipse center extension.  <br/> |
|4096  <br/> |Snap to isometric angles extension.  <br/> |
   

