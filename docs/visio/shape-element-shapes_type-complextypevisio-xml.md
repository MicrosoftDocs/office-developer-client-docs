---
title: "Shape element (Shapes_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 8074bd07-430a-779e-ad1f-e7e3a1c748b1
description: "Contains elements that define a shape in a Master, Page, or group shape element."
---

# Shape element (Shapes_Type complexType) (Visio XML)

Contains elements that define a shape in a **Master**, **Page**, or group shape element.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ShapeSheet_Type](shapesheet_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Shape" type="ShapeSheet_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes. |
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-elementvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property. |
|[Data1](data1-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape. |
|[Data2](data2-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape. |
|[Data3](data3-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape. |
|[ForeignData](foreigndata-element-shapesheet_type-complextypevisio-xml.md) <br/> |[ForeignData_Type](foreigndata_type-complextypevisio-xml.md) <br/> |Contains a MIME (Multipurpose Internet Mail Extensions) encoded BLOB of picture data, such as Windows metafile, bitmap, or OLE data. |
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Specifies a collection of related properties. |
|[Shapes](shapes-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes. |
|[Text](text-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Text_Type](text_type-complextypevisio-xml.md) <br/> |Contains the text of a shape. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |A flag indicating whether the element is deleted locally. |Values of the xsd:boolean type. |
|FillStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits fill formatting. |Values of the xsd:unsignedInt type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element. |Values of the xsd:unsignedInt type. |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the name has been customized by the user. |Values of the xsd:boolean type. |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the universal name has been customized by the user.. |Values of the xsd:boolean type. |
|LineStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits line formatting. |Values of the xsd:unsignedInt type. |
|Master  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the Master element from which the shape inherits its data. |Values of the xsd:unsignedInt type. |
|MasterShape  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the Master element from which the shape inherits its data. |Values of the xsd:unsignedInt type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element. |Values of the xsd:string type. |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element. |Values of the xsd:string type. |
|TextStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits text formatting. |Values of the xsd:unsignedInt type. |
|Type  <br/> |xsd:token  <br/> |optional  <br/> |The type of a shape. It may be one of the following values: Group, Shape, Guide, or Foreign. |Values of the xsd:token type. |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> |A GUID (globally unique identifier) assigned to the shape. |Values of the xsd:string type. |
   

