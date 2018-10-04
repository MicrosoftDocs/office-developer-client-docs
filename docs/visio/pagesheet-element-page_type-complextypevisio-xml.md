---
title: "PageSheet element (Page_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 99a6549b-099b-1546-cc30-db0010fe3ce1
description: "Specifies the properties of the drawing page associated with the drawing page."
---

# PageSheet element (Page_Type complexType) ('Visio XML')

Specifies the properties of the drawing page associated with the drawing page.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |pages.xml  <br/> |
   
## Definition

```XML
< xs:element name="PageSheet" type="PageSheet_Type" minOccurs="0" maxOccurs="1" >
</xs:element > 
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Page](page-element-pages_type-complextypevisio-xml.md) <br/> |[Page_Type](page_type-complextypevisio-xml.md) <br/> |Contains elements that define a page in the document.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|FillStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of the style sheet from which to inherit fill formatting. It MUST be the value of the **ID** attribute associated with a **StyleSheet_Type** in the drawing.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|LineStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of the style sheet from which to inherit line formatting. It MUST be the value of the **ID** attribute associated with a **StyleSheet_Type** in the drawing.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|TextStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of the style sheet from which to inherit text formatting. It MUST be the value of the **ID** attribute associated with a **StyleSheet_Type** in the drawing.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> |The unique ID of the element within its parent element.  <br/> |Values of the xsd:string type.  <br/> |
   

