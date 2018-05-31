---
title: "tp element (Text_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: b13b9328-c6a0-e282-257c-2de55901df6a
description: "Specifies the beginning of a tabs properties run. The run is defined to the end of the text or until the next tag."
---

# tp element (Text_Type complexType) ('Visio XML')

Specifies the beginning of a tabs properties run. The run is defined to the end of the text or until the next tag.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[tp_Type](tp_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="tp" type="tp_Type" minOccurs="0" maxOccurs="unbounded" ></xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Text](text-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Text_Type](text_type-complextypevisio-xml.md) <br/> |Contains the text of a shape.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|IX  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The zero-based index of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

