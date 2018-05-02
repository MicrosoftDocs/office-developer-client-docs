---
title: "Row element (Geometry Section) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 2b273958-1997-7c63-4a61-d231f023a81f
description: "Contains rows that list the coordinates of the vertices for the lines and arcs that make up the shape."
---

# Row element (Geometry Section) ('Visio XML')

Contains rows that list the coordinates of the vertices for the lines and arcs that make up the shape.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[GeometryRow_Type](geometry_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Row" type="GeometryRow_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Contains rows that list the coordinates of the vertices for the lines and arcs that make up the shape.  <br/> |
   
### Child elements

> [!NOTE]
> The Cell element is the only child of this element. Depending on the "T" attribute of this element, the meaning of the Cell elements differ. In the table below, parathetical text in the element name corresponds to the "T" value to which the topic applies. 
  
|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell element (ArcTo Row)](arcto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates and bow of a circular arc.  <br/> |
|[Cell element (Ellipse Row)](ellipse-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the ellipse's center point and two points on the ellipse.  <br/> |
|[Cell element (EllipticalArcTo Row)](ellipticalarcto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x- and y-coordinates of an elliptical arc's endpoint, x- and y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes.  <br/> |
|[Cell element (InfiniteLine Row)](infiniteline-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of two points on an infinite line.  <br/> |
|[Cell element (LineTo Row)](lineto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x-and y-coordinates of the ending vertex of a straight line segment.  <br/> |
|[Cell element (MoveTo Row)](moveto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the first vertex of a shape, or represents the x- and y-coordinates of the first vertex after a break in a path.  <br/> |
|[Cell element (NURBSTo Row)](nurbsto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates, position of the second to last knot, position of the last weight, position of the first knot, position of the first weight, and the formula for a nonuniform rational B-spline (NURBS).  <br/> |
|[Cell element (PolyLineTo Row)](polylineto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x- and y-coordinates of the last point of a polyline and a polyline formula.  <br/> |
|[Cell element (RelCubBezTo Row)](relcubbezto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the endpoint of a cubic Bézier curve relative to the shape's width and height, the x- and y-coordinates of the control point of the beginning of the curve relative shape's width and height, and the x- and y-coordinates of the control point of the ending of the curve relative shape's width and height.  <br/> |
|[Cell element (RelQuadBezTo Row)](relquadbezto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height and the x- and y-coordinates of the control point of the curve relative shape's width and height.  <br/> |
|[Cell element (RelEllipticalArcTo Row)](relellipticalarcto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x- and y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- and y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes.  <br/> |
|[Cell element (RelLineTo Row)](rellineto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x-and y-coordinates of the ending vertex of a straight line segment relative to a shape's width and height.  <br/> |
|[Cell element (RelMoveTo Row)](relmoveto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the first vertex of a shape or the x- and y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape.  <br/> |
|[Cell element (RelQuadBezTo Row)](relquadbezto-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains the x- and y-coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height and the x- and y-coordinates of the control point of the curve relative shape's width and height.  <br/> |
|[Cell element (SplineKnot Row)](splineknot-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x- and y-coordinates for a spline's control point and a spline's knot.  <br/> |
|[Cell element (SplineStart Row)](splinestart-row-geometry-section.md) <br/> |[Cell_Type](http://msdn.microsoft.com/library/6f23bcc4-af93-4023-a380-3e78a228e166%28Office.15%29.aspx) <br/> |Contains x- and y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, and the degree of the spline.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether a row that would otherwise be inherited from a master shape has been deleted.  <br/> |Values of the xsd:boolean type.  <br/> |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the one-based identifier for the row. It should be unqiue and greater than other identifiers in the same section.The IX attribute is only used for the Character, Connection, Field, FillGradient, Geometry, Layer, LineGradient, Paragraph, Reviewer, Scratch, and Tabs sections. A row can only have one of the IX or N attributes.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|LocalName  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-dependent name of the row.  <br/> |Values of the xsd:string type.  <br/> |
|N  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-independent name of the row.The N attribute is only used for the User, Property, Actions, Control, Connection, Hyperlink, and ActionTag sections. A row can only have one of the IX or N attributes.  <br/> |Values of the xsd:string type.  <br/> |
|T  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the type of the geometric path represented by the row and used in geometry visualization. The T attribute is only used for the Geometry section.  <br/> |Values of the xsd:string type.  <br/> |
   
## Remarks

The **T** attribute of this **Row** element must be one of a limited set of values that correspond to ShapeSheet rows. Refer to the table below to determine the values of the **T** attribute that are permitted for this **Row** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|ArcTo  <br/> |Contains the x- and y-coordinates and bow of a circular arc.  <br/> |[ArcTo Row (Geometry Section)](arcto-row-geometry-section.md) <br/> |
|Ellipse  <br/> |Contains the x- and y-coordinates of the ellipse's center point and two points on the ellipse.  <br/> |[Ellipse Row (Geometry Section)](ellipse-row-geometry-section.md) <br/> |
|EllipticalArcTo  <br/> |Contains x- and y-coordinates of an elliptical arc's endpoint, x- and y-coordinates of the control points on the arc, angle from the x-axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes.  <br/> |[EllipticalArcTo Row (Geometry Section)](ellipticalarcto-row-geometry-section.md) <br/> |
|InfiniteLine  <br/> |Contains the x- and y-coordinates of two points on an infinite line.  <br/> |[InfiniteLine Row (Geometry Section)](http://msdn.microsoft.com/library/Contains the x- and y-coordinates of two points on an infinite line.%28Office.15%29.aspx) <br/> |
|LineTo  <br/> |Contains x-and y-coordinates of the ending vertex of a straight line segment.  <br/> |[LineTo Row (Geometry Section)](lineto-row-geometry-section.md) <br/> |
|MoveTo  <br/> |Contains the x- and y-coordinates of the first vertex of a shape, or represents the x- and y-coordinates of the first vertex after a break in a path.  <br/> |[MoveTo Row (Geometry Section)](moveto-row-geometry-section.md) <br/> |
|NURBSTo  <br/> |Contains the x- and y-coordinates, position of the second to last knot, position of the last weight, position of the first knot, position of the first weight, and the formula for a nonuniform rational B-spline (NURBS).  <br/> |[NURBSTo Row (Geometry Section)](nurbsto-row-geometry-section.md) <br/> |
|PolylineTo  <br/> |Contains x- and y-coordinates of the last point of a polyline and a polyline formula.  <br/> |[PolylineTo Row (Geometry Section)](polylineto-row-geometry-section.md) <br/> |
|RelCubBezTo  <br/> |Contains the x- and y-coordinates of the endpoint of a cubic Bézier curve relative to the shape's width and height, the x- and y-coordinates of the control point of the beginning of the curve relative shape's width and height, and the x- and y-coordinates of the control point of the ending of the curve relative shape's width and height.  <br/> |[RelCubBezTo Row (Geometry Section)](relcubbezto-row-geometry-section.md) <br/> |
|RelEllipticalArcTo  <br/> |Contains x- and y-coordinates of an elliptical arc's endpoint relative to the shape's width and height, x- and y-coordinates of the control points on the arc relative to the shape's width and height, angle from the x-axis to the ellipse's major axis, and ratio between the ellipse's major and minor axes.  <br/> |[RelEllipticalArcTo Row (Geometry Section)](relellipticalarcto-row-geometry-section.md) <br/> |
|RelLineTo  <br/> |Contains x-and y-coordinates of the ending vertex of a straight line segment relative to a shape's width and height.  <br/> |[RelLineTo Row (Geometry Section)](rellineto-row-geometry-section.md) <br/> |
|RelMoveTo  <br/> |Contains the x- and y-coordinates of the first vertex of a shape or the x- and y-coordinates of the first vertex after a break in a path, relative to the height and width of the shape.  <br/> |[RelMoveTo Row (Geometry Section)](relmoveto-row-geometry-section.md) <br/> |
|RelQuadBezTo  <br/> |Contains the x- and y-coordinates of the endpoint of a quadratic Bézier curve relative to the shape's width and height and the x- and y-coordinates of the control point of the curve relative shape's width and height.  <br/> |[RelQuadBezTo Row (Geometry Section)](relquadbezto-row-geometry-section.md) <br/> |
|SplineKnot  <br/> |Contains x- and y-coordinates for a spline's control point and a spline's knot.  <br/> |[SplineKnot Row (Geometry Section)](splineknot-row-geometry-section.md) <br/> |
|SplineStart  <br/> |Contains x- and y-coordinates for a spline's second control point, its second knot, its first knot, the last knot, and the degree of the spline.  <br/> |[SplineStart Row (Geometry Section)](splinestart-row-geometry-section.md) <br/> |
   

