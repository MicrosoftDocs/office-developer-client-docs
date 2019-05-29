---
title: "ValidationProperties element (Validation_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a51a60c9-479b-7d7b-860f-bb46fc8b4d63
description: "Encapsulates the properties that are related to the document's validation."
---

# ValidationProperties element (Validation_Type complexType) (Visio XML)

Encapsulates the properties that are related to the document's validation.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ValidationProperties_Type](validationproperties_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="ValidationProperties" type="ValidationProperties_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Validation](validation-elementvisio-xml.md) <br/> |[Validation_Type](validation_type-complextypevisio-xml.md) <br/> |Stores information about diagram validation for the document.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|LastValidated  <br/> |xsd:dateTime  <br/> |required  <br/> |The date and time that the document was last validated.  <br/> |Values of the xsd:dateTime type.  <br/> |
|ShowIgnored  <br/> |xsd:boolean  <br/> |required  <br/> |Specifies whether to show ignored validation issues in the Issues window.  <br/> |Values of the xsd:boolean type.  <br/> |
   

