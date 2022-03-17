---
title: "PersonEntry element (PersonsList_Type complexType) (Visio XML)"
 
 
ms.date: 02/18/2022
description: "Specifies properties used to identify a mentioned person in comments in a drawing."
---

# PersonEntry element (PersonsList_Type complexType) (Visio XML)

Specifies properties used to identify a mentioned person in comments in a drawing.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[PersonEntry_Type](personentry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |persons.xml  <br/> |
   
## Definition

```XML
<xs:element name="PersonEntry" type="PersonEntry_Type" minOccurs="0" maxOccurs="unbounded" />
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PersonsList](personslist-element-persons_type-complextypevisio-xml.md) <br/> |[PersonsList_Type](personslist_type-complextypevisio-xml.md) <br/> |Specifies the list of persons mentioned in the comments in a drawing. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|DisplayName  <br/> |xsd:string  <br/> |required  <br/> |Full name of the person @mentioned |Values of the xsd:string type. |
|PersonID  <br/> |xsd:unsignedInt  <br/> |required  <br/> | Unique Identifier of the person @mentioned|Values of the xsd:unsignedInt type. |
|ProviderID  <br/> |xsd:string  <br/> |optional  <br/> |ID of the provider|Values of the xsd:string type. |
|UserID  <br/> |xsd:string  <br/> |optional  <br/> |Identifier of the user account|Values of the xsd:string type. |

