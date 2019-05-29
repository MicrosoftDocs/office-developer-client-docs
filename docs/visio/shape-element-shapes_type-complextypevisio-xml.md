---
title: "Shape element (Shapes_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 8074bd07-430a-779e-ad1f-e7e3a1c748b1
description: "Contains elements that define a shape in a Master, Page, or group shape element."
---

# Shape element (Shapes_Type complexType) ('Visio XML')

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
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes.  <br/> |
|[Shapes](shapes-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](cell-elementvisio-xml.md) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |Specifies a single property.  <br/> |
|[Data1](data1-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape.  <br/> |
|[Data2](data2-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape.  <br/> |
|[Data3](data3-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Data_Type](data_type-complextypevisio-xml.md) <br/> |Contains an arbitrary string value that is used to supply additional information about a shape.  <br/> |
|[ForeignData](foreigndata-element-shapesheet_type-complextypevisio-xml.md) <br/> |[ForeignData_Type](foreigndata_type-complextypevisio-xml.md) <br/> |Contains a MIME (Multipurpose Internet Mail Extensions) encoded BLOB of picture data, such as Windows metafile, bitmap, or OLE data.  <br/> |
|[Section](section-element-sheet_type-complextypevisio-xml.md) <br/> |[Section_Type](section_type-complextypevisio-xml.md) <br/> |Specifies a collection of related properties.  <br/> |
|[Shapes](shapes-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Shapes_Type](shapes_type-complextypevisio-xml.md) <br/> |Specifies a collection of shapes.  <br/> |
|[Text](text-element-shapesheet_type-complextypevisio-xml.md) <br/> |[Text_Type](text_type-complextypevisio-xml.md) <br/> |Contains the text of a shape.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> |A flag indicating whether the element is deleted locally.  <br/> |Values of the xsd:boolean type.  <br/> |
|FillStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits fill formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the name has been customized by the user.  <br/> |Values of the xsd:boolean type.  <br/> |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the universal name has been customized by the user..  <br/> |Values of the xsd:boolean type.  <br/> |
|LineStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits line formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Master  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the Master element from which the shape inherits its data.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|MasterShape  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the Master element from which the shape inherits its data.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|TextStyle  <br/> |xsd:unsignedInt  <br/> ||The ID of the StyleSheet from which this shape inherits text formatting.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Type  <br/> |xsd:token  <br/> |optional  <br/> |The type of a shape. It may be one of the following values: Group, Shape, Guide, or Foreign.  <br/> |Values of the xsd:token type.  <br/> |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> |A GUID (globally unique identifier) assigned to the shape.  <br/> |Values of the xsd:string type.  <br/> |
   

