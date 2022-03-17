---
title: "ModernCommentEntry_Type complexType (Visio XML)"
 
 
ms.date: 02/18/2022
---

# ModernCommentEntry_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
 <xs:complexType name="ModernCommentEntry_Type">
		<xs:sequence>
			<xs:element name="MentionsList" type="MentionsList_Type" minOccurs="0" maxOccurs="1" />
			<xs:any minOccurs="0" maxOccurs="unbounded" namespace="##any" processContents="lax" />
		</xs:sequence>
		<xs:attribute name="CommentID" type="xs:unsignedInt" use="required" />
		<xs:attribute name="ParentID" type="xs:unsignedInt" />
		<xs:anyAttribute namespace="##other" processContents="lax" />
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[MentionsList](mentionslist-element-moderncommententry_type-complextypevisio-xml.md) <br/> |[MentionsList_Type](mentionslist_type-complextypevisio-xml.md) <br/> ||
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CommentID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|ParentID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type. |
   

