---
title: "RefBy_Type complexType ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: e2990281-6410-5a35-2b28-3a8b33246c73

---

# RefBy_Type complexType ('Visio XML')

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
      <xs:complexType name="RefBy_Type">
    <xs:attribute name="T"
  type="xsd:string"
     use="required"
    />
    <xs:attribute name="ID"
  type="xsd:unsignedInt"
     use="required"
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
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|T  <br/> |xsd:string  <br/> |required  <br/> ||Values of the xsd:string type.  <br/> |
   

