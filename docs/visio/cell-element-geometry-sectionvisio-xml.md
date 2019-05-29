---
title: "Cell element (Geometry Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 82dcad38-d5fa-4892-91d9-1f3f25f1e600
description: "Defines properties that determine formatting and behavioral properties with respect to the lines and arcs that make up the Geometry Section."
---

# Cell element (Geometry Section) (Visio XML)

Defines properties that determine formatting and behavioral properties with respect to the lines and arcs that make up the Geometry Section.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Cell" type="Cell_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[Geometry_Type](geometry_type-complextypevisio-xml.md) <br/> |Defines properties that determine formatting and behavioral properties with respect to the lines and arcs that make up the Geometry Section.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value.  <br/> |An error message string.  <br/> |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/>  `No Formula` if the formula is locally deleted or blocked  <br/>  `Inh` if the formula is inherited.  <br/> |A formula.  <br/> |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the ShapeSheet cell.  <br/> |The name of the ShapeSheet cell.  <br/> See the Remarks section below.  <br/> |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL.  <br/> |The units of the cell.  <br/> |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell.  <br/> |The value of the ShapeSheet cell.  <br/> |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|NoFill  <br/> |Indicates whether a path can be filled.  <br/> |[NoFill Cell (Geometry Section)](nofill-cell-geometry-section.md) <br/> |
|NoLine  <br/> |Determines whether a line is drawn around the boundary of the path.  <br/> |[NoLine Cell (Geometry Section)](noline-cell-geometry-section.md) <br/> |
|NoQuickDrag  <br/> |Determines whether a shape can be selected or dragged when the user clicks the filled area defined by the Geometry section.  <br/> |[NoQuickDrag Cell (Geometry Section)](noquickdrag-cell-geometry-section.md) <br/> |
|NoShow  <br/> |Indicates whether a path is displayed on the drawing page.  <br/> |[NoShow Cell (Geometry Section)](noshow-cell-geometry-section.md) <br/> |
|NoSnap  <br/> |Determines whether other shapes snap to a path.  <br/> |[NoSnap Cell (Geometry Section)](nosnap-cell-geometry-section.md) <br/> |
   

