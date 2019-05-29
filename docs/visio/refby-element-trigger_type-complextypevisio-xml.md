---
title: "RefBy element (Trigger_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 09f2430a-184d-eaa2-2cb9-51bb24345c51
description: "Specifies a reference to a page in the drawing."
---

# RefBy element (Trigger_Type complexType) (Visio XML)

Specifies a reference to a page in the drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> ||
   
## Definition

```XML
< xs:element name="RefBy" type="RefBy_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Trigger](trigger-elementvisio-xml.md) <br/> |[Trigger_Type](trigger_type-complextypevisio-xml.md) <br/> |Provides instructions to Microsoft Visio to recalculate a relationship between document parts in a Visio file.  <br/> |

   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the ID attribute of a page in the drawing.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|T  <br/> |xsd:string  <br/> |required  <br/> |Specifies the reference type.  <br/> |Values of the xsd:string type.  <br/> |
   

