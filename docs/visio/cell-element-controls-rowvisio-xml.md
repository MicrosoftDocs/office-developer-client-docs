---
title: "Cell element (Controls Row) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 3c04d243-002c-bb00-a4be-0bcb8e156402
description: "Contains a property for a particular control handle defined for a shape."
---

# Cell element (Controls Row) ('Visio XML')

Contains a property for a particular control handle defined for a shape.
  
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
|[Row element (Controls Section)](row-element-controls-sectionvisio-xml.md) <br/> |[ControlRow_Type](controlrow_type-complextypevisio-xml.md) <br/> |Contains a property for a particular control handle defined for a shape.  <br/> |
   
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
|CanGlue  <br/> |Determines whether a control handle can be glued to other shapes.  <br/> |[Can Glue Cell (Controls Section)](can-glue-cell-controls-section.md) <br/> |
|Prompt  <br/> |Represents a descriptive text string that appears as a ToolTip when a user pauses the pointer over a shape's control handle.  <br/> |[Tip Cell (Controls Section)](tip-cell-controls-section.md) <br/> |
|X  <br/> |Represents the x-coordinate that indicates the location of a shape's control handle in local coordinates.  <br/> |[X Cell (Controls Section)](x-cell-controls-section.md) <br/> |
|xCon  <br/> |Specifies the type of behavior the x-coordinate of the control handle exhibits after the handle is moved.  <br/> |None.  <br/> |
|xDyn  <br/> |Represents the x-coordinate for a control handle's anchor point in local coordinates.  <br/> |[X Dynamics Cell (Controls Section)](x-dynamics-cell-controls-section.md) <br/> |
|Y  <br/> |Represents the y-coordinate that indicates the location of a shape's control handle in local coordinates.  <br/> |[Y Cell (Controls Section)](y-cell-controls-section.md) <br/> |
|YCon  <br/> |Specifies the type of behavior the y-coordinate of the control handle will exhibit after the handle is moved.  <br/> |None.  <br/> |
|YDyn  <br/> |Represents the y-coordinate for a control handle's anchor point in local coordinates.  <br/> |[Y Dynamics Cell (Controls Section)](y-dynamics-cell-controls-section.md) <br/> |
   

