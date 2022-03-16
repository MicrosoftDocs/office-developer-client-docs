---
title: "Window element (Windows_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: da776276-e8c2-085b-9b23-e5b1f5ba64cd
description: "Represents an open window in a Microsoft Visio instance. This element contains information necessary to exactly re-create a user interface window in the application workspace when the file is initially opened by Visio."
---

# Window element (Windows_Type complexType) (Visio XML)

Represents an open window in a Microsoft Visio instance. This element contains information necessary to exactly re-create a user interface window in the application workspace when the file is initially opened by Visio.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Window_Type](window_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |windows.xml  <br/> |
   
## Definition

```XML
< xs:element name="Window" type="Window_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Windows](windows-elementvisio-xml.md) <br/> |[Windows_Type](windows_type-complextypevisio-xml.md) <br/> |Contains the **Window** elements for a document. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DynamicGridEnabled](dynamicgridenabled-element-window_type-complextypevisio-xml.md) <br/> |[DynamicGridEnabled_Type](dynamicgridenabled_type-complextypevisio-xml.md) <br/> |Specifies whether the dynamic grid feature is enabled for a document or window. |
|[GlueSettings](gluesettings-element-window_type-complextypevisio-xml.md) <br/> |[GlueSettings_Type](gluesettings_type-complextypevisio-xml.md) <br/> |Specifies the objects that shapes glue to when glue is enabled in the document. |
|[ShowConnectionPoints](showconnectionpoints-element-window_type-complextypevisio-xml.md) <br/> |[ShowConnectionPoints_Type](showconnectionpoints_type-complextypevisio-xml.md) <br/> |Specifies whether connection points are shown in a window. |
|[ShowGrid](showgrid-element-window_type-complextypevisio-xml.md) <br/> |[ShowGrid_Type](showgrid_type-complextypevisio-xml.md) <br/> |Specifies whether a grid is shown in the drawing window. |
|[ShowGuides](showguides-element-window_type-complextypevisio-xml.md) <br/> |[ShowGuides_Type](showguides_type-complextypevisio-xml.md) <br/> |Specifies whether guides are shown in the drawing window. |
|[ShowPageBreaks](showpagebreaks-element-window_type-complextypevisio-xml.md) <br/> |[ShowPageBreaks_Type](showpagebreaks_type-complextypevisio-xml.md) <br/> |Specifies whether page breaks are shown in a window. |
|[ShowRulers](showrulers-element-window_type-complextypevisio-xml.md) <br/> |[ShowRulers_Type](showrulers_type-complextypevisio-xml.md) <br/> |Specifies whether rulers are shown in the drawing window. |
|[SnapAngles](snapangles-element-window_type-complextypevisio-xml.md) <br/> |[SnapAngles_Type](snapangles_type-complextypevisio-xml.md) <br/> |Contains a collection of **SnapAngle** elements. |
|[SnapExtensions](snapextensions-element-window_type-complextypevisio-xml.md) <br/> |[SnapExtensions_Type](snapextensions_type-complextypevisio-xml.md) <br/> |Specifies whether a specific snap extension setting is enabled or disabled for the active window. |
|[SnapSettings](snapsettings-element-window_type-complextypevisio-xml.md) <br/> |[SnapSettings_Type](snapsettings_type-complextypevisio-xml.md) <br/> |Specifies the objects that shapes snap to when snap is active in the window. |
|[StencilGroup](stencilgroup-element-window_type-complextypevisio-xml.md) <br/> |[StencilGroup_Type](stencilgroup_type-complextypevisio-xml.md) <br/> |Specifies the group of merged stencil windows of which the window is a member. |
|[StencilGroupPos](stencilgrouppos-element-window_type-complextypevisio-xml.md) <br/> |[StencilGroupPos_Type](stencilgrouppos_type-complextypevisio-xml.md) <br/> |Contains an integer that specifies the relative position of a stencil within a group in a window. |
|[TabSplitterPos](tabsplitterpos-element-window_type-complextypevisio-xml.md) <br/> |[TabSplitterPos_Type](tabsplitterpos_type-complextypevisio-xml.md) <br/> |Specifies the width of the page tab control of a drawing window (as a fraction of the total width of the drawing window). |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Container  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |ID of container: Page, Sheet, or Master. Only relevant and necessary if **ContainerType** is specified. |Values of the xsd:unsignedInt type. |
|ContainerType  <br/> |xsd:token  <br/> |optional  <br/> |May be one of the following values: Document, Page, or Master. Only relevant when **WindowType** is specified as Drawing or Sheet. |Values of the xsd:token type. |
|Document  <br/> |xsd:string  <br/> |optional  <br/> |File path of the document displayed in this window. |Values of the xsd:string type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The unique ID of the element within its parent element. |Values of the xsd:unsignedInt type. |
|Master  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Master ID if this window is displaying a master. |Values of the xsd:unsignedInt type. |
|Page  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Page ID if this window is displaying a page. Relevant only when **WindowType** is specified as Drawing and **ContainerType** is specified as Page. |Values of the xsd:unsignedInt type. |
|ParentWindow  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |ID of window in which this stencil window is contained. Relevant only when **WindowType** is specified as Stencil. |Values of the xsd:unsignedInt type. |
|ReadOnly  <br/> |xsd:boolean  <br/> |optional  <br/> |Read-only flag if this stencil is not a document stencil. |Values of the xsd:boolean type. |
|Sheet  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |ID of sheet in container. Relevant only when Container is specified as Sheet. |Values of the xsd:unsignedInt type. |
|ViewCenterX  <br/> |xsd:double  <br/> |optional  <br/> |**ViewCenterX** and **ViewCenterY** specify a center point on a page that a new view (window) assumes when it is opened initially. |Values of the xsd:double type. |
|ViewCenterY  <br/> |xsd:double  <br/> |optional  <br/> |**ViewCenterX** and **ViewCenterY** specify a center point on a page that a new view (window) assumes when it is opened initially. |Values of the xsd:double type. |
|ViewScale  <br/> |xsd:double  <br/> |optional  <br/> |The default magnification factor to use when a new view (window) of the page is opened. For example, 1 = 100%; 1.5 = 150%, and so on. |Values of the xsd:double type. |
|WindowHeight  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Height of the window rectangle. |Values of the xsd:unsignedInt type. |
|WindowLeft  <br/> |xsd:short  <br/> |optional  <br/> |Left coordinate of the window rectangle. |Values of the xsd:short type. |
|WindowState  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |An integer specifying bit flags. |Values of the xsd:unsignedInt type. |
|WindowTop  <br/> |xsd:short  <br/> |optional  <br/> |Top coordinate of the window rectangle. |Values of the xsd:short type. |
|WindowType  <br/> |xsd:token  <br/> |required  <br/> |An enumerated value that may be one of the following: Drawing, Sheet, Stencil, or Icon. |Values of the xsd:token type. |
|WindowWidth  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Width of the window rectangle. |Values of the xsd:unsignedInt type. |
   

