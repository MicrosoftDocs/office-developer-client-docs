---
title: "ModernComments_Type complexType (Visio XML)"
 
 
ms.date: 18/02/2022

---

# ModernComments_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
         <xs:complexType name="ModernComments_Type">
		<xs:sequence>
			<xs:element name="ModernCommentsList" type="ModernCommentsList_Type" minOccurs="0" maxOccurs="1" />
		</xs:sequence>
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[ModernCommentsList](moderncommentslist-element-modernComments_type-complextypevisio-xml.md) <br/> |[ModernCommentsList_Type](moderncommentslist_type-complextypevisio-xml.md) <br/> |Specifies properties used to identify the parent comment and mentions present in the comments in a drawing.|
   
### Attributes

None.
   

