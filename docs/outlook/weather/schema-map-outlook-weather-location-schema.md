---
title: "Schema map (Outlook Weather Location Schema)"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 1a5195ae-7905-477a-7818-9eb3bff64af0
description: "This topic shows the schema definition for the Outlook Weather Location XML Schema."
---

# Schema map (Outlook Weather Location Schema)

This topic shows the schema definition for the Outlook Weather Location XML Schema.
  
```XML
<?xml version="1.0" ?>
<xs:schema
  attributeFormDefault="unqualified" elementFormDefault="qualified"
xmlns:xs="https://www.w3.org/2001/XMLSchema"
targetNamespace= "http://schemas.microsoft.com/office/outlook/15/getweatherlocation.xsd"
xmlns="http://schemas.microsoft.com/office/outlook/15/getweatherlocation.xsd"
>
  <!-- get weather location  -->
  <!-- example query: https://weather.service.msn.com/data.aspx?outputview=search&amp;weasearchstr=tsurumi -->
  
  <xs:element name="weatherdata">
    <xs:annotation>
      <xs:documentation>Defines the weather element.</xs:documentation>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:element name="weather" type="weatherType" maxOccurs="unbounded">
          <xs:annotation>
            <xs:documentation>Specifies the location to report weather on.</xs:documentation>
          </xs:annotation>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:complexType name="weatherType">
    <xs:annotation>
      <xs:documentation> Defines the parameters about the weather conditions of a location.</xs:documentation>
    </xs:annotation>
    <xs:attribute name="weatherlocationname" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the name of the location.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="weatherlocationcode" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies a code that is associated with the location to distinguish multiple locations with the same name. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
  </xs:complexType>
</xs:schema>
```


