---
title: "forecast element (weatherType complexType) (Outlook Weather Information Schema)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9124fa30-d58b-8354-91e9-8d2237a8251d
description: "Specifies the future weather conditions of at least three days ahead including today: Today, Tomorrow, Day after Tomorrow."
---

# forecast element (weatherType complexType) (Outlook Weather Information Schema)

Specifies the future weather conditions of at least three days ahead including today: Today, Tomorrow, Day after Tomorrow.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[forecastType](forecasttype-complextype-outlook-weather-information-schema.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd  <br/> |
|**Schema file** <br/> |getweatherinfo.xsd  <br/> |
   
## Definition

```XML
<xs:element name="forecast"      type="forecastType" minOccurs="3"     maxOccurs="unbounded"    >
  </xs:element>  

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[weather](weather-element-weatherdata-elementoutlook-weather-information-schema.md) <br/> |[weatherType](weathertype-complextype-outlook-weather-information-schema.md) <br/> |Specifies the weather conditions of a location.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|date  <br/> |xs:date  <br/> |required  <br/> |Specifies the date for the forecast.  <br/> |A value of the type xs:date  <br/> |
|day  <br/> |xs:string  <br/> |required  <br/> |Specifies a day for the forecast.  <br/> |A value of the type xs:string  <br/> |
|high  <br/> |xs:integer  <br/> |required  <br/> |Specifies the forecasted highest temperature.  <br/> |A value of the type xs:integer  <br/> |
|low  <br/> |xs:integer  <br/> |required  <br/> |Specifies the forecasted lowest temperature.  <br/> |A value of the type xs:integer  <br/> |
|precip  <br/> |xs:integer  <br/> |required  <br/> |Specifies the percentage possibility of precipitation.  <br/> |A value of the type xs:integer  <br/> |
|shortday  <br/> |xs:string  <br/> |required  <br/> |Specifies a day in abbreviated form.  <br/> |A value of the type xs:string  <br/> |
|skycodeday  <br/> |xs:integer  <br/> |required  <br/> |Specifies a code for the forecasted conditions.  <br/> |A value of the type xs:integer  <br/> |
|skytextday  <br/> |xs:string  <br/> |required  <br/> |Specifies one to two words that describe the forecasted conditions.  <br/> |A value of the type xs:string  <br/> |
   

