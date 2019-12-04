---
title: "Row element (Paragraph Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 00ecaa82-3b40-24cc-91c0-b2562e92161d
description: "Shows the paragraph formatting attributes for the shape's text, such as indents, line spacing, bullets, and horizontal alignment of paragraphs."
---

# Row element (Paragraph Section) (Visio XML)

Shows the paragraph formatting attributes for the shape's text, such as indents, line spacing, bullets, and horizontal alignment of paragraphs.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ParagraphRow_Type](paragraphrow_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Row" type="ParagraphRow_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Shows the paragraph formatting attributes for the shape's text, such as indents, line spacing, bullets, and horizontal alignment of paragraphs.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-element-paragraph-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether a row that would otherwise be inherited from a master shape has been deleted.  <br/> |Values of the xsd:boolean type.  <br/> |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the one-based identifier for the row. It should be unqiue and greater than other identifiers in the same section.The IX attribute is only used for the Character, Connection, Field, FillGradient, Geometry, Layer, LineGradient, Paragraph, Reviewer, Scratch, and Tabs sections. A row can only have one of the IX or N attributes.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|LocalName  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-dependent name of the row.  <br/> |Values of the xsd:string type.  <br/> |
|N  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-independent name of the row.The N attribute is only used for the User, Property, Actions, Control, Connection, Hyperlink, and ActionTag sections. A row can only have one of the IX or N attributes.  <br/> |Values of the xsd:string type.  <br/> |
|T  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the type of the geometric path represented by the row and used in geometry visualization. The T attribute is only used for the Geometry section.  <br/> |Values of the xsd:string type.  <br/> |
   

