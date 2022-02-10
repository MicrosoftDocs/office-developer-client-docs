---
title: "Row element (User-defined Cells Section) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 9fc27888-2809-aa29-4dbb-7e4f8a0c4758
description: "A user-specified piece of information that can be referred to by other cells and add-on tools."
---

# Row element (User-defined Cells Section) (Visio XML)

A user-specified piece of information that can be referred to by other cells and add-on tools.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[UserRow_Type](userrow_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, masters.xml, master#.xml, pages.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Row" type="UserRow_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |A user-specified piece of information that can be referred to by other cells and add-on tools. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-element-user-defined-cells-sectionvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |One property of a user-specified piece of information that can be referred to by other cells and add-on tools. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether a row that would otherwise be inherited from a master shape has been deleted. |Values of the xsd:boolean type. |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the one-based identifier for the row. It should be unqiue and greater than other identifiers in the same section.The IX attribute is only used for the Character, Connection, Field, FillGradient, Geometry, Layer, LineGradient, Paragraph, Reviewer, Scratch, and Tabs sections. A row can only have one of the IX or N attributes. |Values of the xsd:unsignedInt type. |
|LocalName  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-dependent name of the row. |Values of the xsd:string type. |
|N  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the unique language-independent name of the row.The N attribute is only used for the User, Property, Actions, Control, Connection, Hyperlink, and ActionTag sections. A row can only have one of the IX or N attributes. |Values of the xsd:string type. |
|T  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the type of the geometric path represented by the row and used in geometry visualization. The T attribute is only used for the Geometry section. |Values of the xsd:string type. |
   

