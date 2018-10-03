---
title: "Master element (Masters_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: c102fd71-c621-2bde-9fbb-8e9203fdf31e
description: "Contains elements that define a master for the document."
---

# Master element (Masters_Type complexType) ('Visio XML')

Contains elements that define a master for the document.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Master_Type](master_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |masters.xml  <br/> |
   
## Definition

```XML
< xs:element name="Master" type="Master_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Masters](masters-elementvisio-xml.md) <br/> |[Masters_Type](masters_type-complextypevisio-xml.md) <br/> |Contains the **Master** elements for the document.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Connects](connects-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Connects_Type](connects_type-complextypevisio-xml.md) <br/> |Contains a **Connect** element for each connection between two shapes in a drawing.  <br/> |
|[Icon](icon-element-master_type-complextypevisio-xml.md) <br/> |[Icon_Type](icon_type-complextypevisio-xml.md) <br/> |Specifies a MIME (Multipurpose Internet Mail Extensions) encoded binary icon (in .ico format) for a **Master** or **MasterShortcut** element in a document.  <br/> |
|[PageSheet](pagesheet-element-master_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Contains elements that define the page sheet for a **Page** or **Master** element.  <br/> |
|Shapes  <br/> |Shapes_Type  <br/> |Contains a collection of **Shape** elements.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AlignName  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Specifies whether the master's text in the stencil window is aligned left, right, or center.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|BaseID  <br/> |xsd:string  <br/> |optional  <br/> |A GUID (globally unique identifier) that identifies the master across documents.  <br/> |Values of the xsd:string type.  <br/> |
|Hidden  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether the master is hidden in the user interface.  <br/> |Values of the xsd:boolean type.  <br/> |
|IconSize  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |The size of the element's icon.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|IconUpdate  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether the icon is automatically generated from the master itself.  <br/> |Values of the xsd:boolean type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|MatchByName  <br/> |xsd:boolean  <br/> |optional  <br/> |Determines how Microsoft Visio decides if a document master is already present when an instance of a master is dropped on the drawing page.  <br/> |Values of the xsd:boolean type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|PatternFlags  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Determines whether a master behaves as a custom pattern.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|Prompt  <br/> |xsd:string  <br/> |optional  <br/> |The status bar and tool tip prompt for the element.  <br/> |Values of the xsd:string type.  <br/> |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> |A GUID that identifies the master within the document.  <br/> |Values of the xsd:string type.  <br/> |
   

