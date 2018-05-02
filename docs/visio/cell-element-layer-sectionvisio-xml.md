---
title: "Cell element (Layer Section) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: f9896839-ca36-b82b-7412-e57195d4b8e2
description: "Specifies one property for a layer or its properties for a page."
---

# Cell element (Layer Section) ('Visio XML')

Specifies one property for a layer or its properties for a page.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |masters.xml, pages.xml  <br/> |
   
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
|[Row element (Layer Section)](row-element-layer-sectionvisio-xml.md) <br/> |[LayerRow_Type](layerrow_type-complextypevisio-xml.md) <br/> |Specifies one property for a layer or its properties for a page.  <br/> |
   
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
|Active  <br/> |Specifies whether a layer is active.  <br/> |None.  <br/> |
|Color  <br/> |Specifies one of the following: The index of the color in the color table used to display the layer or an RGB value specifying a custom color not in the color table.  <br/> |None.  <br/> |
|ColorTrans  <br/> |Determines the degree of transparency for a layer or shape's text color, from 0 (completely opaque) to 1 (completely transparent).  <br/> |None.  <br/> |
|Glue  <br/> |Specifies whether shapes belonging to the layer can be glued to.  <br/> |None.  <br/> |
|Lock  <br/> |Specifies whether shapes belonging to the layer are locked against being selected or edited.  <br/> |None.  <br/> |
|Name  <br/> |The name of a layer.  <br/> |None.  <br/> |
|NameUniv  <br/> |Specifies the universal name of a layer.  <br/> |None.  <br/> |
|Print  <br/> |Specifies whether shapes belonging to the layer are printed when the drawing is printed.  <br/> |None.  <br/> |
|Snap  <br/> |Specifies whether other shapes can snap to shapes assigned to the layer.  <br/> |None.  <br/> |
|Status  <br/> |Specifies whether the layer is a valid layer for a document.  <br/> |None.  <br/> |
|Visible  <br/> |Specifies whether shapes belonging to the layer are visible on the drawing page.  <br/> |None.  <br/> |
   

