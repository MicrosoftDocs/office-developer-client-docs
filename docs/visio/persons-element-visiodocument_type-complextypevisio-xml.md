---
title: "Persons element (VisioDocument_Type complexType) (Visio XML)"
 

ms.date: 02/18/2022
description: "Specifies properties used to identify the mentioned persons in the comments in a drawing"
---

# Persons element (VisioDocument_Type complexType) (Visio XML)

Specifies properties used to identify the mentioned persons in the comments in a drawing
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Persons_Type](persons_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |persons.xml  <br/> |
   
## Definition

```XML
<xs:element name="Persons" type="Persons_Type" minOccurs="0" maxOccurs="1" />
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[VisioDocument](visiodocument-elementvisio-xml.md) <br/> |[VisioDocument_Type](visiodocument_type-complextypevisio-xml.md) <br/> |The root element of a Microsoft Visio document. |
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PersonsList](personslist-element-persons_type-complextypevisio-xml.md) <br/> |[PersonsList_Type](personslist_type-complextypevisio-xml.md) <br/> |Specifies the list of persons mentioned in the comments in a drawing. |
   
### Attributes

None.
  

