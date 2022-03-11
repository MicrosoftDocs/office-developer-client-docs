---
title: "Comments element (Comments_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: f72ced69-0d49-18cd-f1e6-d0b2cb39b4c0
description: "Specifies properties used to identify the authors and comments in a drawing."
---

# Comments element (Comments_Type complexType) (Visio XML)

Specifies properties used to identify the authors and comments in a drawing.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Comments_Type](comments_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |comments.xml  <br/> |
   
## Definition

```XML
< xs:element name="Comments" type="Comments_Type" >
< /xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[AuthorList](authorlist-element-comments_type-complextypevisio-xml.md) <br/> |[AuthorList_Type](authorlist_type-complextypevisio-xml.md) <br/> |Specifies the authors in a drawing. |
|[CommentList](commentlist-element-comments_type-complextypevisio-xml.md) <br/> |[CommentList_Type](commentlist_type-complextypevisio-xml.md) <br/> |Specifies the comments in a drawing. |
   
### Attributes

None.
  

