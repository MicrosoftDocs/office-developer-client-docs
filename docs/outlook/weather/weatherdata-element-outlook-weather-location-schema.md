---
title: "weatherdata element (Outlook Weather Location Schema)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 14e0c469-31dc-fbe2-0d45-da602df04f13
description: "Defines the weather element."
---

# weatherdata element (Outlook Weather Location Schema)

Defines the weather element.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> ||
|**Namespace** <br/> |https://schemas.microsoft.com/office/outlook/15/getweatherlocation.xsd  <br/> |
|**Schema file** <br/> |getweatherlocation.xsd  <br/> |
   
## Definition

```XML
    <xs:element name="weatherdata"
    >
          <xs:complexType>
          <xs:sequence>
    <xs:element name="weather"
     type="weatherType" maxOccurs="unbounded"
	  >
	</xs:element>
	
      </xs:sequence>
      </xs:complexType>
	</xs:element>
	
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[weather](weather-element-weatherdata-elementoutlook-weather-location-schema.md) <br/> |[weatherType](weathertype-complextype-outlook-weather-location-schema.md) <br/> |Specifies the location to report weather on.  <br/> |
   
### Attributes

None.
  

