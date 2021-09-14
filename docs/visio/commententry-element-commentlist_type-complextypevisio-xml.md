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

|||
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
|[CommentList](commentlist-element-comments_type-complextypevisio-xml.md) <br/> |[CommentList_Type](commentlist_type-complextypevisio-xml.md) <br/> |Specifies the comments in a drawing.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AuthorID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A one-based value that identifies the author.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|CommentID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A unique value that identifies the comment in a drawing page.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Date  <br/> |xsd:dateTime  <br/> |required  <br/> |Specifies when a comment was created.  <br/> |Values of the xsd:dateTime type.  <br/> |
|Done  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies the current state of the comment.  <br/> |Values of the xsd:boolean type.  <br/> |
|EditDate  <br/> |xsd:dateTime  <br/> |optional  <br/> |Specifies when a comment was last changed.  <br/> |Values of the xsd:dateTime type.  <br/> |
|PageID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A value that identifies the drawing page the comment is on.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ShapeID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |A value that identifies the shape the comment is on. If no ShapeID is specified, the comment refers to the drawing page.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

