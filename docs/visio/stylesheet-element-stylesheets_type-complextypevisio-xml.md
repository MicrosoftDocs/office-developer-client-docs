---
title: "StyleSheet element (StyleSheets_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 323e1ccd-8ddd-46d3-1032-5d68d01cf4bd
description: "Represents a style defined in a document."
---

# StyleSheet element (StyleSheets_Type complexType) ('Visio XML')

Represents a style defined in a document.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[StyleSheet_Type](stylesheet_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="StyleSheet" Type="StyleSheet_Type" minOccurs="0" maxOccurs="unbounded" ></xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[StyleSheets](stylesheets-element-visiodocument_type-complextypevisio-xml.md) <br/> |[StyleSheets_Type](stylesheets_type-complextypevisio-xml.md) <br/> |Contains a collection of **StyleSheet** elements for the document.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-elementvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property.  <br/> |
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Specifies a collection of related properties.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|FillStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the StyleSheet element from which this style inherits fill formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the name has been customized by the user.  <br/> |Values of the xsd:boolean type.  <br/> |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the universal name has been customized by the user.  <br/> |Values of the xsd:boolean type.  <br/> |
|LineStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the StyleSheet element from which this style inherits line formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|TextStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the StyleSheet element from which this style inherits text formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

