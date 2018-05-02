---
title: "Cell element (RelEllipticalArcTo Row) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: beaa8860-807e-c8dd-8a59-29cd0f91ba45
description: "Contains x- or y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- or y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes."
---

# Cell element (RelEllipticalArcTo Row) ('Visio XML')

Contains x- or y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- or y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Cell" type="Cell_Type" minOccurs="0" maxOccurs="unbounded">
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[RelEllipticalArcTo_Type](relellipticalarcto_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- or y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes.  <br/> |
   
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
|X  <br/> |The x-coordinate of the ending vertex on an arc relative to the width of the shape.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|Y  <br/> |The y-coordinate of the ending vertex on an arc relative to the height of the shape.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|A  <br/> |The x-coordinate of the arc's control point relative to the shape's width; a point on the arc.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|B  <br/> |The y-coordinate of an arc's control point relative to the shape's width.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|C  <br/> |The angle of an arc's major axis relative to the x-axis of its parent.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|D  <br/> |The ratio of an arc's major axis to its minor axis.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
   

