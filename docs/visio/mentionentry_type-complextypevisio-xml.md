---
title: "MentionEntry_Type complexType (Visio XML)"
 

ms.date: 02/18/2022

---

# MentionEntry_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
     	<xs:complexType name="MentionEntry_Type">
		<xs:sequence>
			<xs:any minOccurs="0" maxOccurs="unbounded" namespace="##any" processContents="lax" />
		</xs:sequence>
		<xs:attribute name="MentionCheckSum" type="xs:unsignedInt" use="required" />
		<xs:attribute name="MentionPersonID" type="xs:unsignedInt" use="required" />
		<xs:attribute name="MentionID" type="xs:unsignedInt" use="required" />
		<xs:attribute name="StartIndex" type="xs:unsignedInt" use="required" />
		<xs:attribute name="Length" type="xs:unsignedInt" use="required" />
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
|MentionCheckSum  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|MentionPersonID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|MentionID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|StartIndex  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|Length  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
   

