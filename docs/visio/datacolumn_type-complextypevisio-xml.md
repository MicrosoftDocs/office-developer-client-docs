---
title: "DataColumn_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: bee50623-cdf7-b9d7-867a-70c86922cbac

---

# DataColumn_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
      <xs:complexType name="DataColumn_Type">
    <xs:attribute name="ColumnNameID"
  type="xsd:string"
     use="required"
    />
    <xs:attribute name="Name"
  type="xsd:string"
     use="required"
    />
    <xs:attribute name="Label"
  type="xsd:string"
     use="required"
    />
    <xs:attribute name="OrigLabel"
  type="xsd:string"
    />
    <xs:attribute name="LangID"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="Calendar"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="DataType"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="UnitType"
  type="xsd:string"
    />
    <xs:attribute name="Currency"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="Degree"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="DisplayWidth"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="DisplayOrder"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="Mapped"
  type="xsd:boolean"
    />
    <xs:attribute name="Hyperlink"
  type="xsd:boolean"
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
|Calendar  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type.  <br/> |
|ColumnNameID  <br/> |xsd:string  <br/> |required  <br/> ||Values of the xsd:string type.  <br/> |
|Currency  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type.  <br/> |
|DataType  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type.  <br/> |
|Degree  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|DisplayOrder  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|DisplayWidth  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|Hyperlink  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|Label  <br/> |xsd:string  <br/> |required  <br/> ||Values of the xsd:string type.  <br/> |
|LangID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|Mapped  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|Name  <br/> |xsd:string  <br/> |required  <br/> ||Values of the xsd:string type.  <br/> |
|OrigLabel  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|UnitType  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
   

