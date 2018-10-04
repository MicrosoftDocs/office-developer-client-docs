---
title: "Windows element ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 1880734a-f086-ce6c-5a93-47851bcdd99d
description: "Contains the Window elements for a document."
---

# Windows element ('Visio XML')

Contains the **Window** elements for a document. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Windows_Type](windows_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |windows.xml  <br/> |
   
## Definition

```XML
<xs:element name="Windows" type="Windows_Type" >
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Window](window-element-windows_type-complextypevisio-xml.md) <br/> |[Window_Type](window_type-complextypevisio-xml.md) <br/> |Represents an open window in a Microsoft Visio instance.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ClientHeight  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Represents the height dimension of a display area  <br/> |Values of the xsd:unsignedShort type.  <br/> |
|ClientWidth  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Represents the width dimension of a display area  <br/> |Values of the xsd:unsignedShort type.  <br/> |
   

