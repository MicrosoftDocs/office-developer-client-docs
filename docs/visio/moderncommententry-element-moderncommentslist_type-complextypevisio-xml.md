---
title: "ModernCommentEntry element (ModernCommentsList_Type complexType) (Visio XML)"
 

ms.date: 18/02/2022
description: "Specifies properties used to identify parent comment and list of mentions in a comment in a drawing."
---

# ModernCommentEntry element (ModernCommentsList_Type complexType) (Visio XML)

Specifies properties used to identify parent comment of a comment and list of mentions present in a comment in a drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ModernCommentEntry_Type](moderncommententry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |moderncomments.xml  <br/> |
   
## Definition

```XML
<xs:element name="ModernCommentEntry" type="ModernCommentEntry_Type" minOccurs="0" maxOccurs="unbounded" />
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[ModernCommentsList](moderncommentslist-element-modernComments_type-complextypevisio-xml.md) <br/> |[ModernCommentsList_Type](moderncommentslist_type-complextypevisio-xml.md) <br/> |Specifies properties used to identify parent comment and list of mentions in all the comments in a drawing. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[MentionsList](mentionslist-element-moderncommententry_type-complextypevisio-xml.md) <br/> |[MentionsList_Type](mentionslist_type-complextypevisio-xml.md) <br/> |Specifies the list of mentions in a comment in a drawing. |
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CommentID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A unique value that identifies the comment in the drawing. |Values of the xsd:unsignedInt type. |
|ParentID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |A unique value that identifies the parent comment in the drawing. |Values of the xsd:unsignedInt type. |

