---
title: "Cell element (Character Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6b452591-cf0c-9e1c-c203-e9cf608d3cc3
description: "Specifies a formatting attribute for a shape's text run, such as font, color, style, case, position relative to the baseline, or point size."
---

# Cell element (Character Section) (Visio XML)

Specifies a formatting attribute for a shape's text run, such as font, color, style, case, position relative to the baseline, or point size.
  
## Element information

|||
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
|[Row element (Character Section)](row-element-character-sectionvisio-xml.md) <br/> |[CharacterRow_Type](characterrow_type-complextypevisio-xml.md) <br/> |Specifies a formatting attribute for a shape's text run, such as font, color, style, case, position relative to the baseline, or point size.  <br/> |
   
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
|AsianFont  <br/> |Contains the enumeration of the font used to format a text run containing Asian characters.  <br/> |[AsianFont Cell (Character Section)](asianfont-cell-character-section.md) <br/> |
|Case  <br/> |Determines the case of a shape's text run.  <br/> |[Case Cell (Character Section)](case-cell-character-section.md) <br/> |
|Color  <br/> |Determines the color used for a shape's text run.  <br/> |[Color Cell (Character Section)](color-cell-character-section.md) <br/> |
|ColorTrans  <br/> |Determines the degree of transparency for a layer or shape's text run color, from 0 (completely opaque) to 1 (completely transparent).  <br/> |None.  <br/> |
|ComplexScriptFont  <br/> |Contains the number of the font used to format a text run composed of complex script characters.  <br/> |[ComplexScriptFont Cell (Character Section)](complexscriptfont-cell-character-section.md) <br/> |
|ComplexScriptSize  <br/> |The size of the font used to format a text run composed of complex script characters.  <br/> |[ComplexScriptSize Cell (Character Section)](complexscriptsize-cell-character-section.md) <br/> |
|DblUnderline  <br/> |Determines whether the range of a text run has a double underline below it.  <br/> |[DoubleULine Cell (Character Section)](doubleuline-cell-character-section.md) <br/> |
|DoubleStrikethrough  <br/> |Determines whether a text run is formatted as double strikethrough.  <br/> |[DoubleStrikethrough Cell (Character Section)](doublestrikethrough-cell-character-section.md) <br/> |
|Font  <br/> |Represents the number of the font used to format a text run.  <br/> |[Font Cell (Character Section)](font-cell-character-section.md) <br/> |
|FontScale  <br/> |Specifies the font width.  <br/> |None.  <br/> |
|LangID  <br/> |Indicates the language in which a text run was entered.  <br/> |[LangID Cell (Character Section)](langid-cell-character-section.md) <br/> |
|Letterspace  <br/> |Specifies the amount of space between two or more characters. Space can be added or subtracted in 1/20th point increments.  <br/> |None.  <br/> |
|Overline  <br/> |Determines whether a text run has a line above it.  <br/> |[Overline Cell (Character Section)](overline-cell-character-section.md) <br/> |
|Pos  <br/> |Determines the position of a shape's text run relative to the baseline.  <br/> |[Pos Cell (Character Section)](pos-cell-character-section.md) <br/> |
|Size  <br/> |Determines the size of a text run in the shape's text block.  <br/> |[Size Cell (Character Section)](size-cell-character-section.md) <br/> |
|Strikethru  <br/> |Determines whether a text run is formatted as strikethrough.  <br/> |[Strikethru Cell (Character Section)](strikethru-cell-character-section.md) <br/> |
|Style  <br/> |Shows the character formatting applied to a range of a text run in the shape's text block.  <br/> |[Style Cell (Character Section)](style-cell-character-section.md) <br/> |
   

