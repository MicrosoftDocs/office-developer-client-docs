---
title: "Cell element (Layer Section) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: f9896839-ca36-b82b-7412-e57195d4b8e2
description: "Specifies one property for a layer or its properties for a page."
---

# Cell element (Layer Section) (Visio XML)

Specifies one property for a layer or its properties for a page.
  
## Element information

||Value |
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
|[Row element (Layer Section)](row-element-layer-sectionvisio-xml.md) <br/> |[LayerRow_Type](layerrow_type-complextypevisio-xml.md) <br/> |Specifies one property for a layer or its properties for a page. |
   
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
|Active  <br/> |Specifies whether a layer is active. |None. |
|Color  <br/> |Specifies one of the following: The index of the color in the color table used to display the layer or an RGB value specifying a custom color not in the color table. |None. |
|ColorTrans  <br/> |Determines the degree of transparency for a layer or shape's text color, from 0 (completely opaque) to 1 (completely transparent). |None. |
|Glue  <br/> |Specifies whether shapes belonging to the layer can be glued to. |None. |
|Lock  <br/> |Specifies whether shapes belonging to the layer are locked against being selected or edited. |None. |
|Name  <br/> |The name of a layer. |None. |
|NameUniv  <br/> |Specifies the universal name of a layer. |None. |
|Print  <br/> |Specifies whether shapes belonging to the layer are printed when the drawing is printed. |None. |
|Snap  <br/> |Specifies whether other shapes can snap to shapes assigned to the layer. |None. |
|Status  <br/> |Specifies whether the layer is a valid layer for a document. |None. |
|Visible  <br/> |Specifies whether shapes belonging to the layer are visible on the drawing page. |None. |
   

