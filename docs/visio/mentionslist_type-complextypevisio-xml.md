---
title: "MentionsList_Type complexType (Visio XML)"
 

ms.date: 02/18/2022

---

# MentionsList_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
         <xs:complexType name="MentionsList_Type">
		<xs:sequence>
			<xs:element name="MentionEntry" type="MentionEntry_Type" minOccurs="0" maxOccurs="unbounded" />
		</xs:sequence>
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[MentionEntry](mentionentry-element-mentionslist_type-complextypevisio-xml.md) <br/> |[MentionEntry_Type](mentionentry_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

None.
  

