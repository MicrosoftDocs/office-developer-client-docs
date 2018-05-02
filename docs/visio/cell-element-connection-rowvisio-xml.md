---
title: "Cell element (Connection Row) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 7cafaa31-c56b-ebb0-3bfb-c339cc93038e
description: "Contains the x- or y-coordinates, horizontal or vertical direction, or type for a single connection point on a shape."
---

# Cell element (Connection Row) ('Visio XML')

Contains the x- or y-coordinates, horizontal or vertical direction, or type for a single connection point on a shape.
  
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
|[Row element (Connection Section)](row-element-connection-sectionvisio-xml.md) <br/> |[ConnectionRow_Type](connectionrow_type-complextypevisio-xml.md) <br/> |Contains the x- and y-coordinates, horizontal and vertical direction, and type for a single connection point on a shape.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates, horizontal and vertical direction, and type for a single connection point on a shape.  <br/> |
   
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
|AutoGen  <br/> |Specifies whether the connection point is generated automatically. A value of 1 indicates that the connection point is generated automatically.  <br/> |None.  <br/> |
|DirX  <br/> |Determines the x-component for the required alignment vector of a matching connection point.  <br/> |[DirX / A Cell (Connection Points Section)](dirxa-cell-connection-points-section.md) <br/> |
|DirY  <br/> |Determines the y-component for the required alignment vector of a matching connection point.  <br/> |[DirY / B Cell (Connection Points Section)](diryb-cell-connection-points-section.md) <br/> |
|Prompt  <br/> |This attribute is reserved for future use.  <br/> |None.  <br/> |
|Type  <br/> |Determines the connection point type.  <br/> |[Type / C Cell (Connection Points Section)](typec-cell-connection-points-section.md) <br/> |
|X  <br/> |Represents the x-coordinate for a connection point in local coordinates.  <br/> |[X Cell (Connection Points Section)](x-cell-connection-points-section.md) <br/> |
|Y  <br/> |Determines the y-coordinate for a connection point in local coordinates.  <br/> |[Y Cell (Connection Points Section)](y-cell-connection-points-section.md) <br/> |
   

