---
title: "PageContents element (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 818793d6-608e-5f23-eca2-55ce6667050b
description: "Specifies the information about the shapes in a master or drawing page of a drawing."
---

# PageContents element (Visio XML)

Specifies the information about the shapes in a master or drawing page of a drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[PageContents_Type](pagecontents_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="PageContents" type="PageContents_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Connects](connects-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Connects_Type](connects_type-complextypevisio-xml.md) <br/> |Contains a **Connect** element for each connection between two shapes in a drawing.  <br/> |
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes.  <br/> |
   
### Attributes

None.
  

