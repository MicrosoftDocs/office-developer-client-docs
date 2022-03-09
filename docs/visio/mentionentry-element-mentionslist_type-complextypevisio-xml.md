---
title: "MentionEntry element (MentionsList_Type complexType) (Visio XML)"
 
 
ms.date: 02/18/2022
description: "Specifies properties used to identify a mention in a comment in a drawing."
---

# MentionEntry element (MentionsList_Type complexType) (Visio XML)

Specifies properties used to identify a mention in a comment in a drawing.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[MentionEntry_Type](mentionentry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |moderncomments.xml  <br/> |
   
## Definition

```XML
<xs:element name="MentionEntry" type="MentionEntry_Type" minOccurs="0" maxOccurs="unbounded" />
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[MentionsList](mentionslist-element-moderncommententry_type-complextypevisio-xml.md) <br/> |[MentionsList_Type](mentionslist_type-complextypevisio-xml.md) <br/> |Specifies the list of mentions in a comment in a drawing. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|MentionCheckSum  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Hash value of the part of comment text from 0 index or previous mention end index upto the current mention index|Values of the xsd:unsignedInt type. |
|MentionPersonID  <br/> |xsd:unsignedInt  <br/> |required  <br/> | A one-based value that identifies the person|Values of the xsd:unsignedInt type. |
|MentionID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A unique value that identifies a mention in the comments in a drawing|Values of the xsd:unsignedInt type. |
|StartIndex  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Starting postion of a mention in a comment |Values of the xsd:unsignedInt type. |
|Length  <br/> |xsd:unsignedInt  <br/> |required  <br/> | Length of the mention in a commment|Values of the xsd:unsignedInt type. |
   

