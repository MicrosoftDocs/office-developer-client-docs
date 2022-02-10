---
title: "Cell element (Scratch Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: af17b1c5-51ee-f46f-79d0-4f33369b66f1
description: "Specifies a work area for entering and testing formulas that can be referred to by other cells."
---

# Cell element (Scratch Section) (Visio XML)

Specifies a work area for entering and testing formulas that can be referred to by other cells.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, masters.xml, master#.xml, pages.xml, page#.xml  <br/> |
   
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
|[Row element (Scratch Section)](row-element-scratch-sectionvisio-xml.md) <br/> |[ScratchRow_Type](scratch_type-complextypevisio-xml.md) <br/> |Specifies a work area for entering and testing formulas that can be referred to by other cells. |
   
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
   
### Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|A  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
|B  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
|C  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
|D  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
|X  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
|Y  <br/> |A scratch cell that you can use for entering or testing formulas. |[Scratch Section](scratch-section.md) <br/> |
   

