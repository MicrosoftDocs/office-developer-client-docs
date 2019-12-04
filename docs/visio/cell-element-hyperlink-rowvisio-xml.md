---
title: "Cell element (Hyperlink Row) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: d2089db4-39eb-06d3-d2f8-9465baef5c75
description: "Contains the information for a single hyperlink associated with a shape. A shape will contain one Hyperlink row for each hyperlink."
---

# Cell element (Hyperlink Row) (Visio XML)

Contains the information for a single hyperlink associated with a shape. A shape will contain one **Hyperlink** row for each hyperlink. 
  
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
|[Row element (Hyperlink Section)](row-element-hyperlink-sectionvisio-xml.md) <br/> |[HyperlinkRow_Type](hyperlinkrow_type-complextypevisio-xml.md) <br/> |Contains the information for a single hyperlink associated with a shape. A shape will contain one **Hyperlink** row for each hyperlink.  <br/> |
   
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
|Address  <br/> |Specifies a URL address, file name, or UNC path to which to jump.  <br/> |[Address Cell (Hyperlinks Section)](address-cell-hyperlinks-section.md) <br/> |
|Default  <br/> |Determines the default hyperlink for a shape or page.  <br/> |[Default Cell (Hyperlinks Section)](default-cell-hyperlinks-section.md) <br/> |
|Description  <br/> |Represents a descriptive text string for a hyperlink.  <br/> |[Description Cell (Hyperlinks Section)](description-cell-hyperlinks-section.md) <br/> |
|ExtraInfo  <br/> |Represents a string that passes information to be used in resolving a URL, such as the coordinates of an image map.  <br/> |[ExtraInfo Cell (Hyperlinks Section)](extrainfo-cell-hyperlinks-section.md) <br/> |
|Frame  <br/> |Represents the name of a frame to target when the application is open as an Active document in a container application. The default is an empty string.  <br/> |[Frame Cell (Hyperlinks Section)](frame-cell-hyperlinks-section.md) <br/> |
|Invisible  <br/> |Indicates whether a hyperlink appears on the shortcut menu for a shape or page.  <br/> |[Invisible Cell (Hyperlinks Section)](invisible-cell-hyperlinks-section.md) <br/> |
|NewWindow  <br/> |Specifies whether to open the hyperlink in a new window.  <br/> |[NewWindow Cell (Hyperlinks Section)](newwindow-cell-hyperlinks-section.md) <br/> |
|SortKey  <br/> |A number that determines the order of hyperlinks that appear on a shortcut menu.  <br/> |[SortKey Cell (Hyperlinks Section)](sortkey-cell-hyperlinks-section.md) <br/> |
|SubAddress  <br/> |Specifies a location within the target document to link to.  <br/> |[SubAddress Cell (Hyperlinks Section)](subaddress-cell-hyperlinks-section.md) <br/> |
   

