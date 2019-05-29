---
title: "Section element (Sheet_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 2e7e5dcc-f667-a08c-caa0-4b81e3126ef9
description: "Specifies a collection of related properties."
---

# Section element (Sheet_Type complexType) ('Visio XML')

Specifies a collection of related properties.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, masters.xml, master#.xml, pages.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Section" type="Section_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSheet_Type](documentsheet_type-complextypevisio-xml.md) <br/> |Specifies properties of a drawing.  <br/> |
|[PageSheet](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Specifies the properties of a page in a drawing.  <br/> |
|[PageSheet](pagesheet-element-master_type-complextypevisio-xml.md) <br/> |[Master_Type complexType](master_type-complextypevisio-xml.md) <br/> |Specifies the properties of the drawing page associated with the master.  <br/> |
|[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[ShapeSheet_Type](shapesheet_type-complextypevisio-xml.md) <br/> |Specifies a collection of properties associated with a shape.  <br/> |
|[Sheet](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[Sheet_Type](sheet_type-complextypevisio-xml.md) <br/> |Specifies a collection of properties associated with a style, drawing, drawing page, or shape.  <br/> |
|[StyleSheet](stylesheet-element-stylesheets_type-complextypevisio-xml.md) <br/> |[StyleSheet_Type](stylesheet_type-complextypevisio-xml.md) <br/> |Specifies a style sheet.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-elementvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property.  <br/> |
|[Row](https://msdn.microsoft.com/library/c978e3eb-b895-8fb7-e2ba-88c50e57b3db%28Office.15%29.aspx) <br/> |[Row_Type](row_type-complextypevisio-xml.md) <br/> |Specifies a collection of **Cell_Type** elements.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether a collection that would otherwise be inherited has been deleted. It MUST be equal to 0 or 1. A value of 1 specifies that the collection is unused and MUST be ignored. A value of 0 specifies that the collection of properties is valid for the shape. If the **Del** attribute is not present, the value is 0.  <br/> |Values of the xsd:boolean type.  <br/> |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the zero-based index of the element. It MUST be unique amongst all of the **Section_Type** elements with the same **N** attribute of the containing **Sheet_Type**. It MUST be greater than the **IX** attribute of any preceding **Section_Type** element with the same **N** attribute of the containing **Sheet_Type**.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|N  <br/> |xsd:string  <br/> |required  <br/> |Specifies the language-independent name of the collection of properties. It MUST be unique amongst all of the **Section_Type** elements of the containing **Sheet_Type** element, unless it is equal to "Geometry". It MUST be equal to a subheading in **Sections**.  <br/> |Values of the xsd:string type.  <br/> |
   
### Remarks

The **N** attribute of this **Section** element must be one of a limited set of values that correspond to **ShapeSheet** cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Section** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|Actions  <br/> |A collection of properties that are used for formula evaluation. It MUST have a **ShapeSheet_Type** or **PageSheet_Type** parent element.  <br/> |[Actions Section](actions-section.md) <br/> |
|ActionTag  <br/> |A collection of properties that are used for formula evaluation only. It MUST have a **ShapeSheet_Type** or **PageSheet_Type** parent element.  <br/> |[Action Tag Section](action-tag-section.md) <br/> |
|Connections  <br/> |A collection of properties that are used for formula evaluation only. It MUST have a **ShapeSheet_Type** parent element.  <br/> ||
|Controls  <br/> |A collection of properties that are used for formula evaluation only. It MUST have a **ShapeSheet_Type** parent element.  <br/> |[Controls Section](controls-section.md) <br/> |
|Hyperlink  <br/> |A collection of related properties that specify the shape hyperlinks. It MUST have a **ShapeSheet_Type** parent element.  <br/> |[Hyperlinks Section](hyperlinks-section.md) <br/> |
|ShapeData  <br/> |A collection of related properties that specify the shape data. It MUST have a **ShapeSheet_Type** parent element.  <br/> |[Shape Data Section](shape-data-section.md) <br/> |
|User  <br/> |A collection of properties that are used for formula evaluation. It MUST have a **DocumentSheet_Type**, **PageSheet_Type**, or **ShapeSheet_Type** parent element.  <br/> |[User-defined Cells Section](user-defined-cells-section.md) <br/> |
   
The **IX** attribute of this **Section** element must be one of a limited set of values that correspond to **ShapeSheet** cells. Refer to the table below to determine the values of the **IX** attribute that are permitted for this **Section** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|Annotation  <br/> |A collection of properties that contain information about comments inserted into a document page.  <br/> |[Annotation Section](annotation-section.md) <br/> |
|Character  <br/> |A collection of related properties that specify the character properties of the text of a shape. It MUST have a **ShapeSheet_Type** parent element or a **StyleSheet_Type** parent element.  <br/> |[Character Section](character-section.md) <br/> |
|Connections  <br/> |A collection of properties that are used for formula evaluation only. It MUST have a **ShapeSheet_Type** parent element.  <br/> |[Connection Points Section](connection-points-section.md) <br/> |
|Field  <br/> |A collection of related properties that specify the text fields of a shape. It MUST have a **ShapeSheet_Type** parent element.  <br/> |[Text Fields Section](text-fields-section.md) <br/> |
|FillGradient  <br/> |A collection of properties that specify the fill color gradient of a shape. It MUST have a **ShapeSheet_Type** or **StyleSheet_Type** parent element.  <br/> |[Fill Gradient Section](fill-gradient-section.md) <br/> |
|Geometry  <br/> |A collection of related properties that specify the geometry visualization. It MUST have a **ShapeSheet_Type** parent element. The first **Row_Type** child element of this element MUST be of type MoveTo, RelMoveTo, Ellipse, or InfiniteLine.  <br/> |[Geometry Section](geometry-section.md) <br/> |
|Layers  <br/> |A collection of properties that show all layers defined on a drawing page. It MUST be the child of a **PageSheet_Type** element.  <br/> |[Layers Section](layers-section.md) <br/> |
|Line Gradient  <br/> |A collection of related properties that specify the line color gradient of a shape. It MUST have a **ShapeSheet_Type** or **StyleSheet_Type** parent element.  <br/> |[Line Gradient Section](line-gradient-section.md) <br/> |
|Paragraph  <br/> |A collection of related properties that specify the paragraph properties of the text of a shape. It MUST have a **ShapeSheet_Type** parent element or a **StyleSheet_Type** parent element.  <br/> |[Paragraph Section](paragraph-section.md) <br/> |
|Reviewer  <br/> |A collection of properties that are used for formula evaluation. It MUST have a **DocumentSheet_Type** parent element.  <br/> |[Reviewer Section](reviewer-section.md) <br/> |
|Scratch  <br/> |A collection of properties that are used for formula evaluation. It MUST have a **DocumentSheet_Type**, **PageSheet_Type**, or **ShapeSheet_Type** parent element.  <br/> |[Scratch Section](scratch-section.md) <br/> |
|Tabs  <br/> |A collection of related properties that specify the tabs properties of the text of a shape. It MUST have a **ShapeSheet_Type** parent element or a **StyleSheet_Type** parent element.  <br/> |[Tabs Section](tabs-section.md) <br/> |
   

