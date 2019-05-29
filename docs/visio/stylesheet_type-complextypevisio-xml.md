---
title: "StyleSheet_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 06a02d07-920e-7d47-d63a-da3596cf20f6

---

# StyleSheet_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |Sheet_Type  <br/> |
   
## Definition

```XML
      <xs:complexType name="StyleSheet_Type">
        <xs:complexContent>
        <xs:extension base="Sheet_Type">
      
    <xs:attribute name="ID"
  type="xsd:unsignedInt"
     use="required"
    />
    <xs:attribute name="Name"
  type="xsd:string"
    />
    <xs:attribute name="NameU"
  type="xsd:string"
    />
    <xs:attribute name="IsCustomName"
  type="xsd:boolean"
    />
    <xs:attribute name="IsCustomNameU"
  type="xsd:boolean"
    />
        </xs:extension>
        </xs:complexContent>
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
   

