---
title: "Cell element (Ellipse Row) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 210e6731-7c94-90b1-c7c4-635df974fdb6
description: "Contains the x- or y-coordinates of the ellipse's center point and two points on the ellipse."
---

# Cell element (Ellipse Row) (Visio XML)

Contains the x- or y-coordinates of the ellipse's center point and two points on the ellipse.
  
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
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[Ellipse_Type](ellipse_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the ellipse's center point and two points on the ellipse. |
   
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
|X  <br/> |The x-coordinate of the center point. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|Y  <br/> |The y-coordinate of the center point. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|A  <br/> |The x-coordinate of the first point on the ellipse; paired with y-coordinate represented by the B cell. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|B  <br/> |The y-coordinate of the first point on the ellipse; paired with x-coordinate represented by the A cell. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|C  <br/> |The x-coordinate of the second point on the ellipse; paired with y-coordinate represented by the D cell. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|D  <br/> |The y-coordinate of the second point on the ellipse; paired with y-coordinate represented by the C cell. |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
   

