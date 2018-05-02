---
title: "DocumentSheet element (VisioDocument_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 9b8673e1-b913-52db-2d1d-b3e8f4b8f952
description: "Specifies a DocumentSheet structure."
---

# DocumentSheet element (VisioDocument_Type complexType) ('Visio XML')

Specifies a DocumentSheet structure.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[DocumentSheet_Type](documentsheet_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="DocumentSheet" type="DocumentSheet_Type" minOccurs="0" maxOccurs="1" >
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
|[Cell](cell-elementvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a cell in a DocumentSheet.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> |Describes whether the name has been customized by the user.  <br/> |Values of the xsd:Boolean type.  <br/> |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> |Describes whether the universal name has been customized by the user.  <br/> |Values of the xsd:Boolean type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the language-dependent name of the DocumentSheet.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the language- independent name of the DocumentSheet.  <br/> |Values of the xsd:string type.  <br/> |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> |Optional string. A GUID (globally unique identifier) identifying the shape.  <br/> |Values of the xsd:string type.  <br/> |
   

