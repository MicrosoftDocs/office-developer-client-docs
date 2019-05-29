---
title: "FaceName element (FaceNames_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: b1783f05-ced1-917f-8298-eca4ecfa3912
description: "Contains information about a font."
---

# FaceName element (FaceNames_Type complexType) (Visio XML)

Contains information about a font.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[FaceName_Type](facename_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="FaceName" type="FaceName_Type" minOccurs="1" maxOccurs="unbounded" >
</xs:element > 
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[FaceNames](facenames-element-visiodocument_type-complextypevisio-xml.md) <br/> |[FaceNames_Type](facenames_type-complextypevisio-xml.md) <br/> |Contains a collection of **FaceName** elements.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CharSets  <br/> |xsd:string  <br/> |optional  <br/> |The supported character sets of the font.  <br/> |Values of the xsd:string type.  <br/> |
|Flags  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Flags that indicate the following: missing font, default font, asian font, complex font, vertical font, and font type.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |required  <br/> |The name of the font as a UTF-16 Unicode string.  <br/> ||
|Panos  <br/> |xsd:string  <br/> |optional  <br/> |The panose signature for the font. Panose is a classification system for typefaces that categorizes them based upon their visual characteristics.  <br/> |Values of the xsd:string type.  <br/> |
|UnicodeRanges  <br/> |xsd:string  <br/> |optional  <br/> |The supported Unicode ranges of the font.  <br/> |Values of the xsd:string type.  <br/> |
   

