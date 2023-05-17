---
title: "forecastType complexType (Outlook Weather Information Schema)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 6301d6b6-34fa-af8d-e682-605d35cfdf47
description: "Defines the parameters about the forecast weather conditions of a location."
---

# forecastType complexType (Outlook Weather Information Schema)

Defines the parameters about the forecast weather conditions of a location.
  
## Type information

|Property |Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd  <br/> |
|**Schema file** <br/> |getweatherinfo.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
       <xs:complexType name="forecastType">
     <xs:attribute name="shortday"   type="xs:string"      use="required"     />
     <xs:attribute name="day"   type="xs:string"      use="required"     />
     <xs:attribute name="date"   type="xs:date"      use="required"     />
     <xs:attribute name="precip"   type="xs:integer"      use="required"     />
     <xs:attribute name="skytextday"   type="xs:string"      use="required"     />
     <xs:attribute name="skycodeday"   type="xs:integer"      use="required"     />
     <xs:attribute name="high"   type="xs:integer"      use="required"     />
     <xs:attribute name="low"   type="xs:integer"      use="required"     />
       </xs:complexType>

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|date  <br/> |xs:date  <br/> |required  <br/> |Specifies the date for the forecast. |A value of the type xs:date  <br/> |
|day  <br/> |xs:string  <br/> |required  <br/> |Specifies a day for the forecast. |A value of the type xs:string  <br/> |
|high  <br/> |xs:integer  <br/> |required  <br/> |Specifies the forecasted highest temperature. |A value of the type xs:integer  <br/> |
|low  <br/> |xs:integer  <br/> |required  <br/> |Specifies the forecasted lowest temperature. |A value of the type xs:integer  <br/> |
|precip  <br/> |xs:integer  <br/> |required  <br/> |Specifies the percentage possibility of precipitation. |A value of the type xs:integer  <br/> |
|shortday  <br/> |xs:string  <br/> |required  <br/> |Specifies a day in abbreviated form. |A value of the type xs:string  <br/> |
|skycodeday  <br/> |xs:integer  <br/> |required  <br/> |Specifies a code for the forecasted conditions. |A value of the type xs:integer  <br/> |
|skytextday  <br/> |xs:string  <br/> |required  <br/> |Specifies one to two words that describe the forecasted conditions. |A value of the type xs:string  <br/> |
   

