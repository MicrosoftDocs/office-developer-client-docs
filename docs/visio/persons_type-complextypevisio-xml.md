---
title: "Persons_Type complexType (Visio XML)"
 
 
ms.date: 02/18/2022

---

# Persons_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
         	<xs:complexType name="Persons_Type">
		<xs:sequence>
			<xs:element name="PersonsList" type="PersonsList_Type" minOccurs="0" maxOccurs="1" />
		</xs:sequence>
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PersonsList](personslist-element-persons_type-complextypevisio-xml.md) <br/> |[PersonsList_Type](personslist_type-complextypevisio-xml.md) <br/> |Specifies properties used to identify the mentioned persons in the comments in a drawing.|
   
### Attributes

None.
   

