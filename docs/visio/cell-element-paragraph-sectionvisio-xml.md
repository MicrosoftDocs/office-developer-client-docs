---
title: "Cell element (Paragraph Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: de0d3aac-1a0f-1bdf-da94-e6699a55d08e
description: "Specifies a paragraph formatting attribute for the shape's text, such as indents, line spacing, bullets, or horizontal alignment of paragraphs."
---

# Cell element (Paragraph Section) (Visio XML)

Specifies a paragraph formatting attribute for the shape's text, such as indents, line spacing, bullets, or horizontal alignment of paragraphs.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, master#.xml, page#.xml  <br/> |
   
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
|[Row element (Paragraph Section)](row-element-paragraph-sectionvisio-xml.md) <br/> |[ParagraphRow_Type](paragraphrow_type-complextypevisio-xml.md) <br/> |Specifies a paragraph formatting attribute for the shape's text, such as indents, line spacing, bullets, or horizontal alignment of paragraphs. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value. |An error message string. |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/>  `No Formula` if the formula is locally deleted or blocked  <br/>  `Inh` if the formula is inherited. |A formula. |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the ShapeSheet cell. |The name of the ShapeSheet cell. See the Remarks section below. |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL. |The units of the cell. |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell. |The value of the ShapeSheet cell. |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|Bullet  <br/> |Determines the bullet style. |[Bullet Cell (Paragraph Section)](bullet-cell-paragraph-section.md) <br/> |
|BulletFont  <br/> |Represents the number of the font used to format the text when a custom bullet string is specified and the value in the Bullet cell is non-zero. |[BulletFont Cell (Paragraph Section)](bulletfont-cell-paragraph-section.md) <br/> |
|BulletFontSize  <br/> |Specifies the size of a bullet. |[BulletSize Cell (Paragraph Section)](bulletsize-cell-paragraph-section.md) <br/> |
|BulletStr  <br/> |Allows you to create a custom bullet style. |[BulletString Cell (Paragraph Section)](bulletstring-cell-paragraph-section.md) <br/> |
|Flags  <br/> |Indicates whether the text direction is left to right or right to left. |[Flags Cell (Paragraph Section)](flags-cell-paragraph-section.md) <br/> |
|HorzAlign  <br/> |Determines the horizontal alignment of text in the shape's text block. |[HAlign Cell (Paragraph Section)](halign-cell-paragraph-section.md) <br/> |
|IndFirst  <br/> |Represents the distance the first line of each paragraph in the shape's text block is indented from the left indent of the paragraph. This value is independent of the scale of the drawing. If the drawing is scaled, the first line indent remains the same. |[IndFirst Cell (Paragraph Section)](indfirst-cell-paragraph-section.md) <br/> |
|IndLeft  <br/> |Represents the distance all lines of text in a paragraph are indented from the left margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the left indent remains the same. |[IndLeft Cell (Paragraph Section)](indleft-cell-paragraph-section.md) <br/> |
|IndRight  <br/> |Represents the distance all lines of text in a paragraph are indented from the right margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the right indent remains the same. |[IndRight Cell (Paragraph Section)](indright-cell-paragraph-section.md) <br/> |
|SpAfter  <br/> |Determines the amount of space inserted after each paragraph in the shape's text block, in addition to any space from the SpLine cell and, if it is the last paragraph in a text block, the BottomMargin cell. |[SpAfter Cell (Paragraph Section)](spafter-cell-paragraph-section.md) <br/> |
|SpBefore  <br/> |Determines the amount of space inserted before each paragraph in the shape's text block, in addition to any space from the SpLine cell if it is the first paragraph in a text block, the TopMargin cell. |[SpBefore Cell (Paragraph Section)](spbefore-cell-paragraph-section.md) <br/> |
|SpLine  <br/> |Determines the distance between one line of text and the next, expressed as a percentage, where 100% is the height of a text line. |[SpLine Cell (Paragraph Section)](spline-cell-paragraph-section.md) <br/> |
|TextPosAfterBullet  <br/> |Represents the distance between the first line of the paragraph and the bullet. |[TextPosAfterBullet Cell (Paragraph Section)](textposafterbullet-cell-paragraph-section.md) <br/> |
   

