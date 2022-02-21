---
title: "ModernCommentsList_Type complexType (Visio XML)"
 

ms.date: 02/18/2022
---

# ModernCommentsList_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
        <xs:complexType name="ModernCommentsList_Type">
		<xs:sequence>
			<xs:element name="ModernCommentEntry" type="ModernCommentEntry_Type" minOccurs="0" maxOccurs="unbounded" />
		</xs:sequence>
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[ModernCommentEntry](moderncommententry-element-moderncommentslist_type-complextypevisio-xml.md) <br/> |[ModernCommentEntry_Type](moderncommententry_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

None.
  


