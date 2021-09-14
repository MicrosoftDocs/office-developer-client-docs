---
title: "Cell element (Shape Data Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 98643832-7861-385d-3a52-0060ea413e2e
description: "Specifies one property of the shape data."
---

# Cell element (Shape Data Section) (Visio XML)

Specifies one property of the shape data.
  
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
|[Row element (Shape Data Section)](row-element-shape-data-sectionvisio-xml.md) <br/> |[Shape Data_Type](propertyrow_type-complextypevisio-xml.md) <br/> |Specifies one shape data entry for associating data with a shape.  <br/> |
   
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
|Calendar  <br/> |Specifies the type of calendar used when the Type of a shape data item is Date.  <br/> |[Calendar Cell (Shape Data Section)](calendar-cell-shape-data-section.md) <br/> |
|DataLinked  <br/> |Indicates whether Shape Data row is currently linked to a field in a Data Recordset.  <br/> ||
|Format  <br/> |Specifies the formatting of a shape data item that is a string, a fixed list, a number, a variable list, a date or time, a duration, or a currency.  <br/> |[Format Cell (Shape Data Section)](format-cell-shape-data-section.md) <br/> |
|Invisible  <br/> |Specifies whether the shape data item is visible in the Shape Data window.  <br/> |[Invisible Cell (Shape Data Section)](invisible-cell-shape-data-section.md) <br/> |
|Label  <br/> |Specifies the label that appears to users in the Shape Data window. A label consists of alphanumeric characters, including the underscore (_) character.  <br/> |[Label Cell (Shape Data Section)](label-cell-shape-data-section.md) <br/> |
|LangID  <br/> |Indicates the language in which the shape data value was entered.  <br/> |[LangID Cell (Shape Data Section)](langid-cell-shape-data-section.md) <br/> |
|Prompt  <br/> |Specifies descriptive or instructional text that appears as a tip when the mouse is paused over a value in the Shape Data window.  <br/> |[Prompt Cell (Shape Data Section)](prompt-cell-shape-data-section.md) <br/> |
|SortKey  <br/> |Evaluates to a string that influences the order in which items in the Shape Data window are listed.  <br/> |[SortKey Cell (Shape Data Section)](sortkey-cell-shape-data-section.md) <br/> |
|Type  <br/> |Specifies a data type for the shape data value.  <br/> |[Type Cell (Shape Data Section)](type-cell-shape-data-section.md) <br/> |
|Value  <br/> |Contains the shape data item's value as entered in the Define Shape Data dialog box.  <br/> |[Value Cell (Shape Data Section)](value-cell-shape-data-section.md) <br/> |
|Verify  <br/> |Specifies whether the user is queried to enter custom property information for a shape when an instance is created or the shape is duplicated or copied.  <br/> |None.  <br/> |
   

