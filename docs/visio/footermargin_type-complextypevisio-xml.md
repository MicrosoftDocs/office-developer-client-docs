---
title: "FooterMargin_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: db8d1e5b-cd29-f9ff-994a-25c28672db81

---

# FooterMargin_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |xsd:double  <br/> |
   
## Definition

```XML
      <xs:complexType name="FooterMargin_Type">
        <xs:complexContent>
        <xs:extension base="xsd:double">
      
    <xs:attribute name="Unit"
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
|Unit  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
   

