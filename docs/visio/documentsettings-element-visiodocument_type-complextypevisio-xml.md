---
title: "DocumentSettings element (VisioDocument_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 46712e1f-4e02-974f-c224-85db47666ae1
description: "Contains elements that specify document settings."
---

# DocumentSettings element (VisioDocument_Type complexType) (Visio XML)

Contains elements that specify document settings.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[DocumentSettings_Type](documentsettings_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="DocumentSettings" type="DocumentSettings_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[VisioDocument](visiodocument-elementvisio-xml.md) <br/> |[VisioDocument_Type](visiodocument_type-complextypevisio-xml.md) <br/> |The root element of a Microsoft Visio document.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[AttachedToolbars](attachedtoolbars-element-documentsettings_type-complextypevisio-xml.md) <br/> |[AttachedToolbars_Type](attachedtoolbars_type-complextypevisio-xml.md) <br/> |A MIME (Multipurpose Internet Mail Extensions) encoded Microsoft Visio user interface (VSU) file representing custom toolbars.  <br/> |
|[CustomMenusFile](custommenusfile-element-documentsettings_type-complextypevisio-xml.md) <br/> |[CustomMenusFile_Type](custommenusfile_type-complextypevisio-xml.md) <br/> |Contains the name of the Microsoft Visio user interface (.vsu) file that defines custom menus and accelerators for a document.  <br/> |
|[CustomToolbarsFile](customtoolbarsfile-element-documentsettings_type-complextypevisio-xml.md) <br/> |[CustomToolbarsFile_Type](customtoolbarsfile_type-complextypevisio-xml.md) <br/> |Contains the name of the Microsoft Visio user interface (.vsu) file that defines custom toolbars and status bars for a document.  <br/> |
|[DynamicGridEnabled](dynamicgridenabled-element-documentsettings_type-complextypevisio-xml.md) <br/> |[DynamicGridEnabled_Type](dynamicgridenabled_type-complextypevisio-xml.md) <br/> |Specifies whether the dynamic grid feature is enabled for a document or window.  <br/> |
|[GlueSettings](gluesettings-element-documentsettings_type-complextypevisio-xml.md) <br/> |[GlueSettings_Type](gluesettings_type-complextypevisio-xml.md) <br/> |Specifies the objects that shapes glue to when glue is enabled in the document.  <br/> |
|[ProtectBkgnds](protectbkgnds-element-documentsettings_type-complextypevisio-xml.md) <br/> |[ProtectBkgnds_Type](protectbkgnds_type-complextypevisio-xml.md) <br/> |Specifies whether the user is prevented from deleting or editing background pages.  <br/> |
|[ProtectMasters](protectmasters-element-documentsettings_type-complextypevisio-xml.md) <br/> |[ProtectMasters_Type](protectmasters_type-complextypevisio-xml.md) <br/> |Specifies whether the user is prevented from creating, editing, or deleting masters. Regardless of this setting, the user can still create instances of masters.  <br/> |
|[ProtectShapes](protectshapes-element-documentsettings_type-complextypevisio-xml.md) <br/> |[ProtectShapes_Type](protectshapes_type-complextypevisio-xml.md) <br/> |Specifies whether the user is prevented from selecting shapes that have their **LockSelect** element set to 1.  <br/> |
|[ProtectStyles](protectstyles-element-documentsettings_type-complextypevisio-xml.md) <br/> |[ProtectStyles_Type](protectstyles_type-complextypevisio-xml.md) <br/> |Specifies whether the user is prevented from creating or editing styles.  <br/> |
|[SnapAngles](snapangles-element-documentsettings_type-complextypevisio-xml.md) <br/> |[SnapAngles_Type](snapangles_type-complextypevisio-xml.md) <br/> |Contains a collection of **SnapAngle** elements.  <br/> |
|[SnapExtensions](snapextensions-element-documentsettings_type-complextypevisio-xml.md) <br/> |[SnapExtensions_Type](snapextensions_type-complextypevisio-xml.md) <br/> |Specifies whether a specific snap extension setting is enabled or disabled for the active window.  <br/> |
|[SnapSettings](snapsettings-element-documentsettings_type-complextypevisio-xml.md) <br/> |[SnapSettings_Type](snapsettings_type-complextypevisio-xml.md) <br/> |Specifies the objects that shapes snap to when snap is active in the window.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|DefaultFillStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of a **StyleSheet** element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|DefaultGuideStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of a **StyleSheet** element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|DefaultLineStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of a **StyleSheet** element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|DefaultTextStyle  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of a **StyleSheet** element.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|TopPage  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the ID of the page that should be displayed when the document is opened by Microsoft Visio.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

