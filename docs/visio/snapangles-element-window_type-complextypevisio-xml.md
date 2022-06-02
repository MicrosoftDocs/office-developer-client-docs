---
title: "SnapAngles element (Window_Type complexType) (Visio XML)"
description: "Describes the definition and element information for SnapAngles element (Window_Type complexType), which contains a collection of SnapAngle elements."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 5997f374-303a-92b6-6dd3-87ef81104af4
---

# SnapAngles element (Window_Type complexType) (Visio XML)

Contains a collection of **SnapAngle** elements. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[SnapAngles_Type](snapangles_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |windows.xml  <br/> |
   
## Definition

```XML
< xs:element name="SnapAngles" type="SnapAngles_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Window](window-element-windows_type-complextypevisio-xml.md) <br/> |[Window_Type](window_type-complextypevisio-xml.md) <br/> |Represents an open window in a Microsoft Visio instance. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[SnapAngle](snapangle-element-snapangles_type-complextypevisio-xml.md) <br/> |[SnapAngle_Type](snapangle_type-complextypevisio-xml.md) <br/> |Contains a floating point number that specifies a snap angle in degrees. |
   
### Attributes

None.
  

