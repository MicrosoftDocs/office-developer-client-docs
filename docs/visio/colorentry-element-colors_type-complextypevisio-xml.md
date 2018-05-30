---
title: "ColorEntry element (Colors_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 3f325ad8-bbc7-28bf-9e48-1fde4fbdbdc0
description: "Contains a color table entry."
---

# ColorEntry element (Colors_Type complexType) ('Visio XML')

Contains a color table entry.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ColorEntry_Type](colorentry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="ColorEntry" type="ColorEntry_Type" minOccurs="1" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Colors](colors-element-visiodocument_type-complextypevisio-xml.md) <br/> |[Colors_Type](colors_type-complextypevisio-xml.md) <br/> |Contains the document's color table.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|IX  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The zero-based index of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|RGB  <br/> |xsd:string  <br/> |required  <br/> |The hexadecimal value of the color table entry.  <br/> |Values of the xsd:string type.  <br/> |
   

