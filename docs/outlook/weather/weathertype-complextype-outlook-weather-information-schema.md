---
title: "weatherType complexType (Outlook Weather Information Schema)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: b94d848e-868a-5d5e-ad82-39ed9bd5b357
description: "Specifies the weather conditions of a location."
---

# weatherType complexType (Outlook Weather Information Schema)

Specifies the weather conditions of a location.
  
## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd  <br/> |
|**Schema file** <br/> |getweatherinfo.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
           <xs:complexType name="weatherType">
           <xs:sequence>
     <xs:element name="current"      type="currentType">
  </xs:element>  
     <xs:element name="forecast"      type="forecastType" minOccurs="3"     maxOccurs="unbounded"    >
  </xs:element>  
       </xs:sequence>
     <xs:attribute name="weatherlocationcode"   type="xs:string"      use="required"     />
     <xs:attribute name="timezone"   type="xs:integer"      use="required"     />
     <xs:attribute name="attribution"   type="xs:string"      use="required"     />
     <xs:attribute name="degreetype"   type="xs:string"      use="required"     />
     <xs:attribute name="imagerelativeurl"   type="xs:string"      use="required"     />
     <xs:attribute name="url"   type="xs:string"      use="required"     />
     <xs:attribute name="weatherlocationname"   type="xs:string"      use="required"     />
       </xs:complexType>

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
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
   

