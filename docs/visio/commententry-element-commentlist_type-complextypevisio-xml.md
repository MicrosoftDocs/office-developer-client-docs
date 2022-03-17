---
title: "CommentEntry element (CommentList_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: b0653622-fa94-4889-68c2-94f3e7a83119
description: "Specifies properties used to identify a comment in a drawing."
---

# CommentEntry element (CommentList_Type complexType) (Visio XML)

Specifies properties used to identify a comment in a drawing.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[CommentEntry_Type](commententry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |comments.xml  <br/> |
   
## Definition

```XML
< xs:element name="CommentEntry" type="CommentEntry_Type" minOccurs="0" maxOccurs="unbounded" >
< /xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[CommentList](commentlist-element-comments_type-complextypevisio-xml.md) <br/> |[CommentList_Type](commentlist_type-complextypevisio-xml.md) <br/> |Specifies the comments in a drawing. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AuthorID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A one-based value that identifies the author. |Values of the xsd:unsignedInt type. |
|CommentID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A unique value that identifies the comment in a drawing page. |Values of the xsd:unsignedInt type. |
|Date  <br/> |xsd:dateTime  <br/> |required  <br/> |Specifies when a comment was created. |Values of the xsd:dateTime type. |
|Done  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies the current state of the comment. |Values of the xsd:boolean type. |
|EditDate  <br/> |xsd:dateTime  <br/> |optional  <br/> |Specifies when a comment was last changed. |Values of the xsd:dateTime type. |
|PageID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A value that identifies the drawing page the comment is on. |Values of the xsd:unsignedInt type. |
|ShapeID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |A value that identifies the shape the comment is on. If no ShapeID is specified, the comment refers to the drawing page. |Values of the xsd:unsignedInt type. |
   

