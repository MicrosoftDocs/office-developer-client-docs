---
title: "Cell element (RelMoveTo Row) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 8e91497c-0aa1-2021-9317-cf989e5b84a3
description: "Contains the x- or y-coordinates of the first vertex of a shape, or the x- or y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape."
---

# Cell element (RelMoveTo Row) (Visio XML)

Contains the x- or y-coordinates of the first vertex of a shape, or the x- or y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape.
  
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
|[Row element (Geometry)](row-element-geometry-sectionvisio-xml.md) <br/> |[RelMoveTo_Type](relmoveto_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the first vertex of a shape, or the x- or y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a page. |
   
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
|X  <br/> |If the **RelMoveTo** row is the first row in the section, the **X** cell represents the x-coordinate of the first vertex of a shape relative to the width of the shape. If the **RelMoveTo** row appears between two rows, the **X** cell represents the x-coordinate of the first vertex after the break in the path. |[RelMoveTo Row (Geometry Section)](relmoveto-row-geometry-section.md) <br/> |
|Y  <br/> |If the **RelMoveTo** row is the first row in the section, the **Y** cell represents the y-coordinate of the first vertex of a shape relative to the height of the shape. If the **RelMoveTo** row appears between two rows, the **Y** cell represents the y-coordinate of the first vertex after the break in the path. |[RelMoveTo Row (Geometry Section)](relmoveto-row-geometry-section.md) <br/> |
   

