---
title: "SnapSettings element (Window_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 7b87a244-b331-7e93-d304-239f8ca77061
description: "Specifies the objects that shapes snap to when snap is active in the window."
---

# SnapSettings element (Window_Type complexType) (Visio XML)

Specifies the objects that shapes snap to when snap is active in the window.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[SnapSettings_Type](snapsettings_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |windows.xml  <br/> |
   
## Definition

```XML
< xs:element name="SnapSettings" type="SnapSettings_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Window](window-element-windows_type-complextypevisio-xml.md) <br/> |[Window_Type](window_type-complextypevisio-xml.md) <br/> |Represents an open window in a Microsoft Visio instance. |
   
### Child elements

None.
  
### Attributes

None.
  
## Remarks

The value may be a sum of the values in the following table.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Snap to nothing. |
|1  <br/> |Snap to ruler subdivisions. |
|2  <br/> |Snap to grid. |
|4  <br/> |Snap to guides. |
|8  <br/> |Snap to selection handles. |
|16  <br/> |Snap to vertices. |
|32  <br/> |Snap to connection points. |
|256  <br/> |Snap to visible edges of shapes. |
|512  <br/> |Snap to alignment box. |
|1024  <br/> |Snap to shape extensions options. |
|32768  <br/> |Snap disabled. |
|65536  <br/> |Snap to intersections. |
   

