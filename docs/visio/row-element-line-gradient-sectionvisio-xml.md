---
title: "Row element (Line Gradient Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 4d823766-5cb0-925c-f622-18025f44426c
description: "Contains the color, transparency, and position of a gradient stop for a line gradient."
---

# Row element (Line Gradient Section) (Visio XML)

Contains the color, transparency, and position of a gradient stop for a line gradient.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[LineGradientRow_Type](linegradientrow_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Row" type="LineGradientRow_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Contains the color, transparency, and position of a gradient stop for a line gradient. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-element-line-gradient-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether a row that would otherwise be inherited from a master shape has been deleted. |Values of the xsd:boolean type. |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the one-based identifier for the row. It should be unqiue and greater than other identifiers in the same section.The IX attribute is only used for the Character, Connection, Field, FillGradient, Geometry, Layer, LineGradient, Paragraph, Reviewer, Scratch, and Tabs sections. A row can only have one of the IX or N attributes. |Values of the xsd:unsignedInt type. |
|LocalName  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-dependent name of the row. |Values of the xsd:string type. |
|N  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-independent name of the row.The N attribute is only used for the User, Property, Actions, Control, Connection, Hyperlink, and ActionTag sections. A row can only have one of the IX or N attributes. |Values of the xsd:string type. |
|T  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the type of the geometric path represented by the row and used in geometry visualization. The T attribute is only used for the Geometry section. |Values of the xsd:string type. |
   

