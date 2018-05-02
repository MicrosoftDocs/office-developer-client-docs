---
title: "Connects element (PageContents_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 398c141c-8a40-7605-254a-2ee7cc0a7af5
description: "Contains a Connect element for each connection between two shapes in a drawing."
---

# Connects element (PageContents_Type complexType) ('Visio XML')

Contains a **Connect** element for each connection between two shapes in a drawing. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Connects_Type](connects_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Connects" type="Connects_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[MasterContents](mastercontents-elementvisio-xml.md) <br/> |[PageContents_Type](pagecontents_type-complextypevisio-xml.md) <br/> |Specifies the information about the shapes in a master or drawing page of a drawing.  <br/> |
|[PageContents](pagecontents-elementvisio-xml.md) <br/> |[PageContents_Type](pagecontents_type-complextypevisio-xml.md) <br/> |Specifies the information about the shapes in a master or drawing page of a drawing.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Connect](connect-element-connects_type-complextypevisio-xml.md) <br/> |[Connect_Type](connect_type-complextypevisio-xml.md) <br/> |Represents a connection between two shapes in a drawing, such as a line and a box in an organization chart.  <br/> |
   
### Attributes

None.
  

