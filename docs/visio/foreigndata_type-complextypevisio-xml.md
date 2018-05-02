---
title: "ForeignData_Type complexType ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 21b394a6-6f95-fc17-482c-4cb648a0d9bb

---

# ForeignData_Type complexType ('Visio XML')

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="ForeignData_Type">
          
          <xs:sequence>
    <xs:element name="Rel"  type="Rel_Type"
     minOccurs="1"
     maxOccurs="1"
    >
    </xs:element>
    
      </xs:sequence>
    <xs:attribute name="ForeignType"
  type="xsd:token"
     use="required"
    />
    <xs:attribute name="ObjectType"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="ShowAsIcon"
  type="xsd:boolean"
    />
    <xs:attribute name="ObjectWidth"
  type="xsd:double"
    />
    <xs:attribute name="ObjectHeight"
  type="xsd:double"
    />
    <xs:attribute name="MappingMode"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="ExtentX"
  type="xsd:double"
    />
    <xs:attribute name="ExtentY"
  type="xsd:double"
    />
    <xs:attribute name="CompressionType"
  type="xsd:token"
    />
    <xs:attribute name="CompressionLevel"
  type="xsd:double"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Rel](rel-element-foreigndata_type-complextypevisio-xml.md) <br/> |[Rel_Type](rel_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CompressionLevel  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type.  <br/> |
|CompressionType  <br/> |xsd:token  <br/> |optional  <br/> ||Values of the xsd:token type.  <br/> |
|ExtentX  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type.  <br/> |
|ExtentY  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type.  <br/> |
|ForeignType  <br/> |xsd:token  <br/> |required  <br/> ||Values of the xsd:token type.  <br/> |
|MappingMode  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type.  <br/> |
|ObjectHeight  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type.  <br/> |
|ObjectType  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|ObjectWidth  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type.  <br/> |
|ShowAsIcon  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
   

