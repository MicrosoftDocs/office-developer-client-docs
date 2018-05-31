---
title: "RefBy element (Cell_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: ea2a63d3-d319-4420-1929-013dc832b308
description: "Specifies a reference to a page in the drawing."
---

# RefBy element (Cell_Type complexType) ('Visio XML')

Specifies a reference to a page in the drawing.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, masters.xml, master#.xml, pages.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="RefBy" type="RefBy_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell element (Action Tag Section)](cell-element-action-tag-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Defines one property for an action tag on a shape or page.  <br/> |
|[Cell element (Actions Row)](cell-element-actions-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies one property of an action associated with a custom command on a shortcut or action tag menu.  <br/> |
|[Cell element (ArcTo Row)](cell-element-arcto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x coordinate, y coordinate, or bow of a circular arc.  <br/> |
|[Cell element (Character Section)](cell-element-character-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a formatting attribute for a shape's text run, such as font, color, style, case, position relative to the baseline, or point size.  <br/> |
|[Cell element (Connection Row)](cell-element-connection-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates, horizontal or vertical direction, or type for a single connection point on a shape.  <br/> |
|[Cell element (Controls Row)](cell-element-controls-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains a property for a particular control handle defined for a shape.  <br/> |
|[Cell element (Ellipse Row)](cell-element-ellipse-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the ellipse's center point and two points on the ellipse.  <br/> |
|[Cell element (EllipticalArcTo Row)](cell-element-ellipticalarcto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates of an elliptical arc's endpoint, x- or y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes.  <br/> |
|[Cell element (Field Section)](cell-element-field-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Displays functions and formulas inserted in the shape's text by using the Field dialog box.  <br/> |
|[Cell element (Fill Gradient Section)](cell-element-fill-gradient-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the color, transparency, and position of a gradient stop for a fill gradient.  <br/> |
|[Cell element (Geometry Section)](cell-element-geometry-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Defines properties that determine formatting and behavioral properties with respect to the lines and arcs that make up the Geometry Section.  <br/> |
|[Cell element (Hyperlink Row)](cell-element-hyperlink-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the information for a single hyperlink associated with a shape. A shape will contain one Hyperlink row for each hyperlink.  <br/> |
|[Cell element (InfiniteLine Row)](cell-element-infiniteline-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of two points on an infinite line.  <br/> |
|[Cell element (Layer Section)](cell-element-layer-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies one property for a layer or its properties for a page.  <br/> |
|[Cell element (Line Gradient Section)](cell-element-line-gradient-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the color, transparency, or position of a gradient stop for a line gradient.  <br/> |
|[Cell element (LineTo Row)](cell-element-lineto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x-or y-coordinates of the ending vertex of a straight line segment.  <br/> |
|[Cell element (MoveTo Row)](cell-element-moveto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the first vertex of a shape, or represents the x- or y-coordinates of the first vertex after a break in a path.  <br/> |
|[Cell element (NURBSTo Row)](cell-element-nurbsto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates, position of the second to last knot, position of the last weight, position of the first knot, position of the first weight, or the formula for a nonuniform rational B-spline (NURBS).  <br/> |
|[Cell element (Paragraph Section)](cell-element-paragraph-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a paragraph formatting attribute for the shape's text, such as indents, line spacing, bullets, or horizontal alignment of paragraphs.  <br/> |
|[Cell element (PolyLineTo Row)](cell-element-splineknot-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates of the last point of a polyline or a polyline formula.  <br/> |
|[Cell element (RelCubBezTo Row)](cell-element-relcubbezto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the endpoint of a cubic Bézier curve relative to the shape's width and height, the x- or y-coordinates of the control point of the beginning of the curve relative shape's width and height, or the x- or y-coordinates of the control point of the ending of the curve relative shape's width and height.  <br/> |
|[Cell element (RelEllipticalArcTo Row)](cell-element-relellipticalarcto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- or y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, or ratio between the ellipse's major and minor axes.  <br/> |
|[Cell element (RelLineTo Row)](cell-element-rellineto-rowvisio-xml.md)[Cell](cell-element-rellineto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x-or y-coordinates of the ending vertex of a straight line segment relative to a shape's width and height.  <br/> |
|[Cell element (RelMoveTo Row)](cell-element-relmoveto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the first vertex of a shape, or the x- or y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape.  <br/> |
|[Cell element (RelQuadBezTo Section](cell-element-relquadbezto-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains the x- or y-coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height or the x- or y-coordinates of the control point of the curve relative shape's width and height.  <br/> |
|[Cell element (Scratch Section)](cell-element-scratch-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a work area for entering and testing formulas that can be referred to by other cells.  <br/> |
|[Cell element (Shape Data Section](cell-element-shape-data-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies one property of the shape data.  <br/> |
|[Cell element (SplineKnot Row)](cell-element-splineknot-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates for a spline's control point or a spline's knot.  <br/> |
|[Cell element (SplineStart Section](cell-element-splinestart-rowvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Contains x- or y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, or the degree of the spline.  <br/> |
|[Cell element (Tabs Section)](cell-element-tabs-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a property that controls shape and style tab stop position or alignment.  <br/> |
|[Cell element (User-defined Cells Section)](cell-element-user-defined-cells-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |One property of a user-specified piece of information that can be referred to by other cells and add-on tools.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the ID of a page in the drawing.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|T  <br/> |xsd:string  <br/> |required  <br/> |Specifies the reference type.  <br/> |Values of the xsd:string type.  <br/> |
   

