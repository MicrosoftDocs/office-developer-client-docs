---
title: "ForeignData element (ShapeSheet_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 59db25bc-0283-6f56-0aa9-9be98a3e9041
description: "Contains a MIME (Multipurpose Internet Mail Extensions) encoded BLOB of picture data, such as Windows metafile, bitmap, or OLE data."
---

# ForeignData element (ShapeSheet_Type complexType) ('Visio XML')

Contains a MIME (Multipurpose Internet Mail Extensions) encoded BLOB of picture data, such as Windows metafile, bitmap, or OLE data.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ForeignData_Type](foreigndata_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="ForeignData" type="ForeignData_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[ShapeSheet_Type](shapesheet_type-complextypevisio-xml.md) <br/> |Contains elements that define a shape in a **Master**, **Page**, or group shape element.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Rel](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[Rel_Type](shapesheet_type-complextypevisio-xml.md) <br/> |Specifies a relationship to a part containing the image data.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CompressionLevel  <br/> |xsd:double  <br/> |optional  <br/> |Specifies the level of compression applied to the file. This attribute is only meaningful if the foreign data is a raster-based foreign object, such as a DIB, JPG, PNG, TIFF, or GIF file.  <br/> |Values of the xsd:double type.  <br/> |
|CompressionType  <br/> |xsd:token  <br/> |optional  <br/> |Specifies the type of compression applied to the file. This attribute is only meaningful if the foreign data is a raster-based foreign object, such as a DIB, JPG, PNG, TIFF, or GIF file  <br/> |Values of the xsd:token type.  <br/> |
|ExtentX  <br/> |xsd:double  <br/> |optional  <br/> |Specifies the horizontal extent of the metafile. This attribute is only meaningful if the foreign data is a metafile.  <br/> |Values of the xsd:double type.  <br/> |
|ExtentY  <br/> |xsd:double  <br/> |optional  <br/> |Specifies the vertical extent of the metafile. This attribute is only meaningful if the foreign data is a metafile.  <br/> |Values of the xsd:double type.  <br/> |
|ForeignType  <br/> |xsd:token  <br/> |required  <br/> |Indicates metafile, EnhMetaFile, Bitmap, Object, or Ink type.  <br/> |Values of the xsd:token type.  <br/> |
|MappingMode  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Specifies the metafile mapping mode. This attribute is only meaningful if the foreign data is a metafile.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|ObjectHeight  <br/> |xsd:double  <br/> |optional  <br/> |Specifies the height of the object in page units. This attribute is only meaningful if the foreign data is an OLE2 embedded object.  <br/> |Values of the xsd:double type.  <br/> |
|ObjectType  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |An integer indicator of object type. Used when Foreign type is object.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ObjectWidth  <br/> |xsd:double  <br/> |optional  <br/> |Specifies the width of the object in page units. This attribute is only meaningful if the foreign data is an OLE2 embedded object.  <br/> |Values of the xsd:double type.  <br/> |
|ShowAsIcon  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether to show or not show embedded data as an icon.  <br/> |Values of the xsd:boolean type.  <br/> |
   

