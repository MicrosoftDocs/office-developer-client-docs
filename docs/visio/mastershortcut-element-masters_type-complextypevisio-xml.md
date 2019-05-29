---
title: "MasterShortcut element (Masters_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 62f0e093-5385-e552-f91a-02a65eb0e6e1
description: "Specifies a master shortcut defined in the document."
---

# MasterShortcut element (Masters_Type complexType) (Visio XML)

Specifies a master shortcut defined in the document.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[MasterShortcut_Type](mastershortcut_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="MasterShortcut" type="MasterShortcut_Type" minOccurs="0" maxOccurs="unbounded" >
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
|[Icon](icon-element-mastershortcut_type-complextypevisio-xml.md) <br/> |[Icon_Type](icon_type-complextypevisio-xml.md) <br/> |Specifies a MIME (Multipurpose Internet Mail Extensions) encoded binary icon (in .ico format) for a **Master** or **MasterShortcut** element in a document.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AlignName  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Specifies whether the element's text in the stencil window is aligned left, right, or center.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|IconSize  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |The size of the element's icon.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |The name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> |The universal name of the element.  <br/> |Values of the xsd:string type.  <br/> |
|PatternFlags  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Determines whether a master behaves as a custom pattern.  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|Prompt  <br/> |xsd:string  <br/> |optional  <br/> |The status bar and tool tip prompt for the element.  <br/> |Values of the xsd:string type.  <br/> |
|ShortcutHelp  <br/> |xsd:string  <br/> |optional  <br/> |A help string for the element.  <br/> |Values of the xsd:string type.  <br/> |
|ShortcutURL  <br/> |xsd:string  <br/> |optional  <br/> |A URL to a **MasterShortcut** element.  <br/> |Values of the xsd:string type.  <br/> |
   

