---
title: "PersonsList_Type complexType (Visio XML)"
 

ms.date: 02/18/2022
---

# PersonsList_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
     <xs:complexType name="PersonsList_Type">
		<xs:sequence>
			<xs:element name="PersonEntry" type="PersonEntry_Type" minOccurs="0" maxOccurs="unbounded" />
		</xs:sequence>
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PersonEntry](personentry-element-personslist_type-complextypevisio-xml.md) <br/> |[PersonEntry_Type](personentry_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

None.
  


