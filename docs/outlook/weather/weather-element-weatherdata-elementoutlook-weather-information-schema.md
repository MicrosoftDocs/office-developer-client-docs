---
title: "weather element (weatherdata element) (Outlook Weather Information Schema)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: de3c35ef-84a3-b991-7c98-3eca720c9ba0
description: "Specifies the weather conditions of a location."
---

# weather element (weatherdata element) (Outlook Weather Information Schema)

Specifies the weather conditions of a location.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[weatherType](weathertype-complextype-outlook-weather-information-schema.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd  <br/> |
|**Schema file** <br/> |getweatherinfo.xsd  <br/> |
   
## Definition

```XML
<xs:element name="weather"      type="weatherType">
  </xs:element>  

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[weatherdata](weatherdata-element-outlook-weather-information-schema.md) <br/> ||Defines the weather element. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[current](current-element-weathertype-complextypeoutlook-weather-information-schema.md) <br/> |[currentType](currenttype-complextype-outlook-weather-information-schema.md) <br/> |Specifies the current weather conditions. |
|[forecast](forecast-element-weathertype-complextypeoutlook-weather-information-schema.md) <br/> |[forecastType](forecasttype-complextype-outlook-weather-information-schema.md) <br/> |Specifies the future weather conditions of at least three days ahead including today: Today, Tomorrow, Day after Tomorrow. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|attribution  <br/> |xs:string  <br/> |required  <br/> |Specifies the source of the weather information. |A value of the type xs:string  <br/> |
|degreetype  <br/> |xs:string  <br/> |required  <br/> |Specifies the unit for the temperature of the location for example, Celsius. |C, F  <br/> |
|imagerelativeurl  <br/> |xs:string  <br/> |required  <br/> |Specifies the URL of the image for the location. |A value of the type xs:string  <br/> |
|timezone  <br/> |xs:integer  <br/> |required  <br/> |Specifies the GMT offset. |A value between -11 and 12 inclusive  <br/> |
|url  <br/> |xs:string  <br/> |required  <br/> |Specifies the URL for the web page of the weather service that contains weather information for the specified location. |A value of the type xs:string  <br/> |
|weatherlocationcode  <br/> |xs:string  <br/> |required  <br/> |Specifies the code that is associated with the location used to distinguish multiple location that have the same name. |A value of the type xs:string  <br/> |
|weatherlocationname  <br/> |xs:string  <br/> |required  <br/> |Specifies the name of the location that appears in the drop-down control. |A value of the type xs:string  <br/> |
   

