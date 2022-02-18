---
title: "PersonEntry_Type complexType (Visio XML)"
 

ms.date: 18/02/2022

---

# PersonEntry_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
     		<xs:complexType name="PersonEntry_Type">
		<xs:sequence>
			<xs:any minOccurs="0" maxOccurs="unbounded" namespace="##any" processContents="lax" />
		</xs:sequence>
		<xs:attribute name="DisplayName" type="xs:string" use="required" />
		<xs:attribute name="PersonID" type="xs:unsignedInt" use="required" />
		<xs:attribute name="ProviderID" type="xs:string" />
		<xs:attribute name="UserID" type="xs:string" />
		<xs:anyAttribute namespace="##other" processContents="lax" />
	</xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|DisplayName  <br/> |xsd:string  <br/> |required  <br/> ||Values of the xsd:string type. |
|PersonID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|ProviderID  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|UserID  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
   

