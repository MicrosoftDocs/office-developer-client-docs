---
title: "DocumentSheet_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 57af2ed5-7d89-9538-e51b-0bc70f067b40

---

# DocumentSheet_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |Sheet_Type  <br/> |
   
## Definition

```XML
      <xs:complexType name="DocumentSheet_Type">
        <xs:complexContent>
        <xs:extension base="Sheet_Type">
      
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
    <xs:attribute name="UniqueID"
  type="xsd:string"
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
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
   

