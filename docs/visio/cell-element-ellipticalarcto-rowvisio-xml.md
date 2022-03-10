---
title: "Cell element (EllipticalArcTo Row) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 3c0aa7a3-cc54-ffac-2c62-917b3d0a357e
description: "Contains x- or y-coordinates of an elliptical arc's endpoint, x- or y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes."
---

# Cell element (EllipticalArcTo Row) (Visio XML)

Contains x- or y-coordinates of an elliptical arc's endpoint, x- or y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes.
  
## Element information

||Value |
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
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[EllipticalArcTo_Type](ellipticalarcto_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates of an elliptical arc's endpoint, x- or y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value. |An error message string. |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/>  `No Formula` if the formula is locally deleted or blocked  <br/>  `Inh` if the formula is inherited. |A formula. |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the ShapeSheet cell. |The name of the ShapeSheet cell. See the Remarks section below. |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL. |The units of the cell. |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell. |The value of the ShapeSheet cell. |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|X  <br/> |The x-coordinate of the ending vertex on an arc. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|Y  <br/> |The y-coordinate of the ending vertex on an arc. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|A  <br/> |The x-coordinate of the arc's control point; a point on the arc. The control point is best located about halfway between the beginning and ending vertices of the arc. Otherwise, the arc may grow to an extreme size in order to pass through the control point, with unpredictable results. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|B  <br/> |The y-coordinate of an arc's control point. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|C  <br/> |The angle of an arc's major axis relative to the x-axis of its parent shape. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|D  <br/> |The ratio of an arc's major axis to its minor axis. Despite the usual meaning of these words, the "major" axis does not have to be greater than the "minor" axis, so this ratio does not have to be greater than 1. Setting this cell to a value less than or equal to 0 or greater than 1000 can lead to unpredictable results. |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
   

