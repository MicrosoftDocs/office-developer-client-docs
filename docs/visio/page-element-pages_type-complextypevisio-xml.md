---
title: "Page element (Pages_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6e4ac41f-3855-05d8-e659-02c265b8750c
description: "Contains elements that define a page in the document."
---

# Page element (Pages_Type complexType) (Visio XML)

Contains elements that define a page in the document.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Page_Type](page_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |pages.xml  <br/> |
   
## Definition

```XML
< xs:element name="Page" type="Page_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Pages](pages-elementvisio-xml.md) <br/> |[Pages_Type](pages_type-complextypevisio-xml.md) <br/> |Contains the **Page** elements for the document. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PageSheet](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Contains elements that define the page sheet for a **Page** element. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Background  <br/> |xsd:boolean  <br/> |optional  <br/> |A flag indicating if the page is a background page. |Values of the xsd:boolean type. |
|BackPage  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of this page's background page. |Values of the xsd:unsignedInt type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element. |Values of the xsd:unsignedInt type. |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the name has been customized by the user. |Values of the xsd:Boolean type. |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> |Indicates whether the universal name has been customized by the user. |Values of the xsd:Boolean type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element. |Values of the xsd:string type. |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element. |Values of the xsd:string type. |
|ReviewerID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the reviewer associated with the markup overlay. |Values of the xsd:unsignedInt type. |
|ViewCenterX  <br/> |xsd:double  <br/> |optional  <br/> |**ViewCenterX** and **ViewCenterY** specify a center point on a page that a new view (window) assumes when it is opened initially. |Values of the xsd:double type. |
|ViewCenterY  <br/> |xsd:double  <br/> |optional  <br/> |**ViewCenterX** and **ViewCenterY** specify a center point on a page that a new view (window) assumes when it is opened initially. |Values of the xsd:double type. |
|ViewScale  <br/> |xsd:double  <br/> |optional  <br/> |The default magnification factor to use when a new view (window) of the page is opened. For example, 1 = 100%; 1.5 = 150%, and so on. |Values of the xsd:double type. |
   

