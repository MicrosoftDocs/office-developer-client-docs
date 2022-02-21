---
title: "ModernComments element (VisioDocument_Type complexType) (Visio XML)"
 

ms.date: 02/18/2022
description: "Specifies properties used to identify the parent comment and mentions present in the comments in a drawing."
---

# ModernComments element (VisioDocument_Type complexType) (Visio XML)

Specifies properties used to identify the parent comment of the comments and mentions present in the comments in a drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ModernComments_Type](moderncomments_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |moderncomments.xml  <br/> |
   
## Definition

```XML
< xs:element name="ModernComments" type="ModernComments_Type" />
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
|[ModernCommentsList](moderncommentslist-element-moderncomments_type-complextypevisio-xml.md) <br/> |[ModernCommentsList_Type](moderncommentslist_type-complextypevisio-xml.md) <br/> |Specifies properties used to identify parent comment and list of mentions in all the comments in a drawing.  |
   
### Attributes

None.
  

