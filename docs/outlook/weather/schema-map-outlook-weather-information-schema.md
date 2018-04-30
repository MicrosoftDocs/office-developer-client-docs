---
title: "Schema map (Outlook Weather Information Schema)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 4b2bf607-7c56-61a0-e40d-54af2b90aa6d
description: "This topic shows the schema definition for the Outlook Weather Information XML Schema."
---

# Schema map (Outlook Weather Information Schema)

This topic shows the schema definition for the Outlook Weather Information XML Schema.
  
```XML
<?xml version="1.0" ?>
<xs:schema
  attributeFormDefault="unqualified" elementFormDefault="qualified"
xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd"
xmlns="http://schemas.microsoft.com/office/outlook/15/getweatherinfo.xsd"
>
  <!-- get weather info  -->
  <!-- http://weather.service.msn.com/data.aspx?src=vista&amp;weadegreetype=C&amp;culture=en-US&amp;wealocations=wc:10109953 -->
  <xs:element name="weatherdata">
    <xs:annotation>
      <xs:documentation>Defines the weather element.</xs:documentation>
    </xs:annotation>
    <xs:complexType>
      <xs:sequence>
        <xs:element name="weather" type="weatherType">
          <xs:annotation>
            <xs:documentation>Specifies the weather conditions of a location.</xs:documentation>
          </xs:annotation>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  
  <xs:complexType name="weatherType">
    <xs:annotation>
      <xs:documentation>Specifies the weather conditions of a location.</xs:documentation>
    </xs:annotation>
    <xs:sequence>
      <xs:element name="current" type="currentType">
        <xs:annotation>
          <xs:documentation>Specifies the current weather conditions.</xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="forecast" type="forecastType" minOccurs="3" maxOccurs="unbounded">
        <xs:annotation>
          <xs:documentation>Specifies the future weather conditions of at least three days ahead including today: Today, Tomorrow, Day after Tomorrow.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    
    <xs:attribute name="weatherlocationcode" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the code that is associated with the location used to distinguish multiple location that have the same name. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="timezone" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the GMT offset.</xs:documentation>
      </xs:annotation>
      <xs:simpleType>
        <xs:restriction base="xs:integer">
          <xs:minInclusive value="-11"/>
          <xs:maxInclusive value="12"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="attribution" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the source of the weather information.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="degreetype" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the unit for the temperature of the location for example, Celsius.</xs:documentation>
      </xs:annotation>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value='C'/>
          <xs:enumeration value='F'/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="imagerelativeurl" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the URL of the image for the location.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="url" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the URL for the web page of the weather service that contains weather information for the specified location.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="weatherlocationname" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the name of the location that appears in the drop-down control.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
  </xs:complexType>
  <xs:complexType name="currentType">
    <xs:annotation>
      <xs:documentation> Defines the parameters about the current weather conditions of a location.</xs:documentation>
    </xs:annotation>
    <xs:attribute name="winddisplay" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>A string that describes the current wind conditions. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="windspeed" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the current numerical wind speed value.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="humidity" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the current numerical humidity value.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="feelslike" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the temperature of how the current weather feels like.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="observationpoint" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies where the current weather information is observed from.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="observationtime" type="xs:time" use="required">
      <xs:annotation>
        <xs:documentation>Specifies when the current weather information is observed at.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="date" type="xs:date" use="required">
      <xs:annotation>
        <xs:documentation>Specifies today's date.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="skytext" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies one to two words describing current weather conditions.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="skycode" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies an integer code for the current weather conditions. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="temperature" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the current temperature of the location.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="shortday" type="xs:string" use="optional">
      <xs:annotation>
        <xs:documentation>Specifies a day in abbreviated form.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="day" type="xs:string" use="optional">
      <xs:annotation>
        <xs:documentation>Specifies a day for the forecast.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
  </xs:complexType>
  
  <xs:complexType name="forecastType">
    <xs:annotation>
      <xs:documentation> Defines the parameters about the forecast weather conditions of a location.</xs:documentation>
    </xs:annotation>
    <xs:attribute name="shortday" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies a day in abbreviated form.</xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="day" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies a day for the forecast. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="date" type="xs:date" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the date for the forecast. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="precip" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the percentage possibility of precipitation. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="skytextday" type="xs:string" use="required">
      <xs:annotation>
        <xs:documentation>Specifies one to two words that describe the forecasted conditions. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="skycodeday" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies a code for the forecasted conditions. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="high" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the forecasted highest temperature. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
    <xs:attribute name="low" type="xs:integer" use="required">
      <xs:annotation>
        <xs:documentation>Specifies the forecasted lowest temperature. </xs:documentation>
      </xs:annotation>
    </xs:attribute>
  </xs:complexType>
</xs:schema>

```


