---
title: "HeaderFooterFont element (HeaderFooter_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 4e69dd4f-7281-e988-b1fd-93ac8c775c03
description: "Specifies the font used for the header and footer text."
---

# HeaderFooterFont element (HeaderFooter_Type complexType) (Visio XML)

Specifies the font used for the header and footer text.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[HeaderFooterFont_Type](headerfooterfont_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="HeaderFooterFont" type="HeaderFooterFont_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[HeaderFooter](headerfooter-element-visiodocument_type-complextypevisio-xml.md) <br/> |[HeaderFooter_Type](headerfooter_type-complextypevisio-xml.md) <br/> |Contains elements for a document's header and footer. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|CharSet  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies the character set of the font. Equivalent to the GDI LOGFONTlfCharSet field. |Values of the xsd:unsignedByte type. |
|ClipPrecision  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies the clipping precision of the font. Equivalent to the GDI LOGFONTlfClipPrecision field. |Values of the xsd:unsignedByte type. |
|Escapement  <br/> |xsd:int  <br/> |optional  <br/> |Specifies the escapement attribute of the font. Equivalent to the GDI LOGFONTlfEscapement field. |Values of the xsd:int type. |
|FaceName  <br/> |xsd:string  <br/> |optional  <br/> |Contains information about a font. |Values of the xsd:string type. |
|Height  <br/> |xsd:int  <br/> |optional  <br/> |Specifies the height of the shape in drawing units. |Values of the xsd:int type. |
|Italic  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies whether the font is italic. Equivalent to the GDI LOGFONTlfItalic field. |Values of the xsd:unsignedByte type. |
|Orientation  <br/> |xsd:int  <br/> |optional  <br/> |Specifies the orientation of the font. Equivalent to the GDI LOGFONTlfOrientation field. |Values of the xsd:int type. |
|OutPrecision  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies the output precision attribute of the font. Equivalent to the GDI LOGFONTlfOutPrecision field. |Values of the xsd:unsignedByte type. |
|PitchAndFamily  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies the pitch and family of the font. Equivalent to the GDI LOGFONTlfPitchAndFamily field. |Values of the xsd:unsignedByte type. |
|Quality  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies the output quality of the font. Equivalent to the GDI LOGFONTlfQuality field. |Values of the xsd:unsignedByte type. |
|StrikeOut  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies whether the font is a strikeout font. Equivalent to the GDI LOGFONTlfStrikeOut field. |Values of the xsd:unsignedByte type. |
|Underline  <br/> |xsd:unsignedByte  <br/> |optional  <br/> |Specifies whether the font is underlined. Equivalent to the GDI LOGFONTlfUnderline field. |Values of the xsd:unsignedByte type. |
|Weight  <br/> |xsd:int  <br/> |optional  <br/> |Specifies the weight of the font. Equivalent to the GDI LOGFONTlfWeight field. |Values of the xsd:int type. |
|Width  <br/> |xsd:int  <br/> |optional  <br/> |Contains the width of the associated shape in drawing units. |Values of the xsd:int type. |
   

