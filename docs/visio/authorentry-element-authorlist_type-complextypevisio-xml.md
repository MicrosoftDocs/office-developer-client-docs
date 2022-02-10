---
title: "AuthorEntry element (AuthorList_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 21ca601b-27f0-b30b-a99e-56359bdf594c
description: "Specifies properties used to identify the author of a comment in a drawing."
---

# AuthorEntry element (AuthorList_Type complexType) (Visio XML)

Specifies properties used to identify the author of a comment in a drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[AuthorEntry_Type](authorentry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |comments.xml  <br/> |
   
## Definition

```XML
< xs:element name="AuthorEntry" type="AuthorEntry_Type" minOccurs="0" maxOccurs="unbounded" >
< /xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[AuthorList](authorlist-element-comments_type-complextypevisio-xml.md) <br/> |[AuthorList_Type](authorlist_type-complextypevisio-xml.md) <br/> |Specifies the authors in a drawing. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A one-based value that identifies the author. |Values of the xsd:unsignedInt type. |
|Initials  <br/> |xsd:string  <br/> |optional  <br/> |The initials of the author. |Values of the xsd:string type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the author. |Values of the xsd:string type. |
|ResolutionID  <br/> |xsd:string  <br/> |optional  <br/> |A unique identifier for the author. |Values of the xsd:string type. |
   

