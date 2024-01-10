---
title: "Cell element (Field Section) (Visio XML)"
description: "Cell element (Field Section) (Visio XML) displays functions and formulas inserted in the shape's text by using the Field dialog box."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 1a51a5ca-6b68-d2d8-befb-2b1d9cda1b8e
---

# Cell element (Field Section) (Visio XML)

Displays functions and formulas inserted in the shape's text by using the Field dialog box.
  
## Element information

||Value |
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
|[Row element (Field Section)](row-element-field-sectionvisio-xml.md) <br/> |[FieldRow_Type](fieldrow_type-complextypevisio-xml.md) <br/> |Displays functions and formulas inserted in the shape's text by using the Field dialog box. |
   
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
|Calendar  <br/> |Determines the calendar that is used for a text field when the data type is Date. |[Calendar Cell (Text Fields Section)](calendar-cell-text-fields-section.md) <br/> |
|Format  <br/> |Specifies the formatting of a text field that is a string, a number, a date or time, a duration, or a currency. |[Format Cell (Text Fields Section)](format-cell-text-fields-section.md) <br/> |
|ObjectKind  <br/> |Indicates the type of text field. |[ObjectKind Cell (Text Fields Section)](objectkind-cell-text-fields-section.md) <br/> |
|Type  <br/> |Specifies a data type for the text field value. |[Type Cell (Text Fields Section)](type-cell-text-fields-section.md) <br/> |
|UICat  <br/> |Determines the category of an inserted field. This cell is used by the Field and Data format dialog boxes to determine the field and category information. |[UICategory Cell (Text Fields Section)](uicategory-cell-text-fields-section.md) <br/> |
|UICod  <br/> |Determines the code of an inserted field. This cell is used by the Field and Data format dialog boxes to determine the field and category information. |[UICode Cell (Text Fields Section)](uicode-cell-text-fields-section.md) <br/> |
|UIFmt  <br/> |Determines the format of an inserted field. This cell is used by the Field and Data format dialog boxes to determine the field and  <br/> |[UIFormat Cell (Text Fields Section)](uiformat-cell-text-fields-section.md) <br/> |
|Value  <br/> |Contains the function for a field. |[Value Cell (Text Fields Section)](value-cell-text-fields-section.md) <br/> |
   

