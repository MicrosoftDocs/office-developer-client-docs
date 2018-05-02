---
title: "FaceNames element (VisioDocument_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 61e30f57-abd6-9378-45ed-51236ab3d3ee
description: "Contains a collection of FaceName elements."
---

# FaceNames element (VisioDocument_Type complexType) ('Visio XML')

Contains a collection of **FaceName** elements. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[FaceNames_Type](facenames_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="FaceNames" type="FaceNames_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[VisioDocument](visiodocument-elementvisio-xml.md) <br/> |[VisioDocument_Type](visiodocument_type-complextypevisio-xml.md) <br/> |The root element of a Microsoft Visio document.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[FaceName](facename-element-facenames_type-complextypevisio-xml.md) <br/> |[FaceName_Type](facename_type-complextypevisio-xml.md) <br/> |Contains information about a font.  <br/> |
   
### Attributes

None.
  

