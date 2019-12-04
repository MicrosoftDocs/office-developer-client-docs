---
title: "cp element (Text_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 4edd0a3f-e433-bf54-34cd-3b05fd10a5a5
description: "Marks the beginning of a character properties run that is formatted according to the corresponding Char element. The run is defined to the end of the text or until the next tag."
---

# cp element (Text_Type complexType) (Visio XML)

Marks the beginning of a character properties run that is formatted according to the corresponding Char element. The run is defined to the end of the text or until the next tag.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[cp_Type](cp_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="cp" type="cp_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
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
|IX  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The Char element index that this property run represents.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

