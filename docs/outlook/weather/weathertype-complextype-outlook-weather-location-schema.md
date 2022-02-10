---
title: "weatherType complexType (Outlook Weather Location Schema)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: f8054fd9-85ba-fcf6-c96d-a54095d5238c
description: "Defines the parameters about the weather conditions of a location."
---

# weatherType complexType (Outlook Weather Location Schema)

Defines the parameters about the weather conditions of a location.
  
## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherlocation.xsd  <br/> |
|**Schema file** <br/> |getweatherlocation.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
       <xs:complexType name="weatherType">
     <xs:attribute name="weatherlocationname"   type="xs:string"      use="required"     />
     <xs:attribute name="weatherlocationcode"   type="xs:string"      use="required"     />
       </xs:complexType>

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|weatherlocationcode  <br/> |xs:string  <br/> |required  <br/> |Specifies a code that is associated with the location to distinguish multiple locations with the same name. |A value of the type xs:string  <br/> |
|weatherlocationname  <br/> |xs:string  <br/> |required  <br/> |Specifies the name of the location. |A value of the type xs:string  <br/> |
   

