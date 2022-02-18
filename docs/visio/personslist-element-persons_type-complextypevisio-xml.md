---
title: "PersonsList element (PersonEntry_Type complexType) (Visio XML)"
 
 
ms.date: 18/02/2022
description: "Specifies the list of persons mentioned in the comments in a drawing."
---

# CommentList element (Comments_Type complexType) (Visio XML)

Specifies the list of persons mentioned in the comments in a drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[MentionsList_Type](personslist_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |persons.xml  <br/> |
   
## Definition

```XML
<xs:element name="PersonsList" type="PersonsList_Type" minOccurs="0" maxOccurs="1" />
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Persons](persons-element-visiodocument_type-complextypevisio-xml.md) <br/> |[Persons_Type](persons_type-complextypevisio-xml.md) <br/> |Specifies properties used to identify mentioned persons in all the comments in a drawing. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PersonEntry](personentry-element-personslist_type-complextypevisio-xml.md) <br/> |[MentionEntry_Type](personentry_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

None.
  

