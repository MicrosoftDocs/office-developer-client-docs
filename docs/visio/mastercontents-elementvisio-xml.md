---
title: "MasterContents element (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 71e75e9a-1392-b40b-1d51-167cd28b2c53
description: "Specifies information about the shapes in a master in a drawing."
---

# MasterContents element (Visio XML)

Specifies information about the shapes in a master in a drawing. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[PageContents_Type](pagecontents_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="MasterContents" type="PageContents_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Connects](connects-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Connects_Type](connects_type-complextypevisio-xml.md) <br/> |Contains a **Connect** element for each connection between two shapes in a drawing. |
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Contains a collection of **Shape** elements. |
   
### Attributes

None.
  

