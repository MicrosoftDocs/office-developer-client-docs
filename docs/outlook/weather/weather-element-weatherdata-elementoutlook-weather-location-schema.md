---
title: "weather element (weatherdata element) (Outlook Weather Location Schema)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 1127956a-37aa-c39e-60b4-343dcc4ead82
description: "Specifies the location to report weather on."
---

# weather element (weatherdata element) (Outlook Weather Location Schema)

Specifies the location to report weather on.
  
## Element information

|Property |Value |
|:-----|:-----|
|**Element type** <br/> |[weatherType](weathertype-complextype-outlook-weather-location-schema.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherlocation.xsd  <br/> |
|**Schema file** <br/> |getweatherlocation.xsd  <br/> |
   
## Definition

```XML
<xs:element name="weather"      type="weatherType" maxOccurs="unbounded"    >
  </xs:element>  

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[weatherdata](weatherdata-element-outlook-weather-location-schema.md) <br/> ||Defines the weather element. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|weatherlocationcode  <br/> |xs:string  <br/> |required  <br/> |Specifies a code that is associated with the location to distinguish multiple locations with the same name. |A value of the type xs:string  <br/> |
|weatherlocationname  <br/> |xs:string  <br/> |required  <br/> |Specifies the name of the location. |A value of the type xs:string  <br/> |
   

