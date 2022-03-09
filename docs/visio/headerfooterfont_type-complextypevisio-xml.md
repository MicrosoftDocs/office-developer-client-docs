---
title: "HeaderFooterFont_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 1e4134be-fb18-768e-b477-f9f40f72548d

---

# HeaderFooterFont_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
      <xs:complexType name="HeaderFooterFont_Type">
    <xs:attribute name="Height"
  type="xsd:int"
    />
    <xs:attribute name="Width"
  type="xsd:int"
    />
    <xs:attribute name="Escapement"
  type="xsd:int"
    />
    <xs:attribute name="Orientation"
  type="xsd:int"
    />
    <xs:attribute name="Weight"
  type="xsd:int"
    />
    <xs:attribute name="Italic"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="Underline"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="StrikeOut"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="CharSet"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="OutPrecision"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="ClipPrecision"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="Quality"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="PitchAndFamily"
  type="xsd:unsignedByte"
    />
    <xs:attribute name="FaceName"
  type="xsd:string"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CharSet  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|ClipPrecision  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|Escapement  <br/> |xsd:int  <br/> |optional  <br/> ||Values of the xsd:int type. |
|FaceName  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|Height  <br/> |xsd:int  <br/> |optional  <br/> ||Values of the xsd:int type. |
|Italic  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|Orientation  <br/> |xsd:int  <br/> |optional  <br/> ||Values of the xsd:int type. |
|OutPrecision  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|PitchAndFamily  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|Quality  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|StrikeOut  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|Underline  <br/> |xsd:unsignedByte  <br/> |optional  <br/> ||Values of the xsd:unsignedByte type. |
|Weight  <br/> |xsd:int  <br/> |optional  <br/> ||Values of the xsd:int type. |
|Width  <br/> |xsd:int  <br/> |optional  <br/> ||Values of the xsd:int type. |
   

