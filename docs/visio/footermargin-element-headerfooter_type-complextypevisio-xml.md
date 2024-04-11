---
title: "FooterMargin element (HeaderFooter_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 047f42cf-4202-50bd-40b4-a71052e2dfb3
description: "Specifies the margin of a document's footer."
---

# FooterMargin element (HeaderFooter_Type complexType) (Visio XML)

Specifies the margin of a document's footer.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[FooterMargin_Type](footermargin_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="FooterMargin" type="FooterMargin_Type" minOccurs="0" maxOccurs="1" >
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
|Unit  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure. The default is IN. |Values of the xsd:string type. |
   

