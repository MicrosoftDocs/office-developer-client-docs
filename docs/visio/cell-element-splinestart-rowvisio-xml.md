---
title: "Cell element (SplineStart Row) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 021536b9-6724-4b8a-35c2-966e456e5232
description: "Contains x- or y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, or the degree of the spline."
---

# Cell element (SplineStart Row) (Visio XML)

Contains x- or y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, or the degree of the spline.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml, page#.xml  <br/> |
   
## Definition

```XML
<xs:element name="Cell" type="Cell_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[SplineStart_Type](splinestart_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, or the degree of the spline. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value. |An error message string. |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/> `No Formula` if the formula is locally deleted or blocked  <br/> `Inh` if the formula is inherited. |A formula. |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the ShapeSheet cell. |The name of the ShapeSheet cell. See the Remarks section below. |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL. |The units of the cell. |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell. |The value of the ShapeSheet cell. |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|X  <br/> |The x-coordinate of a spline's second control point. |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
|Y  <br/> |The y-coordinate of a spline's second control point. |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
|A  <br/> |The second knot of the spline. |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
|B  <br/> |The first knot of a spline. |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
|C  <br/> |The last knot of a spline. |[RelEllipticalArcTo Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
|D  <br/> |The degree of a spline (an integer from 1 to 25). |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
   

