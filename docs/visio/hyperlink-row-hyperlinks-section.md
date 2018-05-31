---
title: "Hyperlink Row (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm3065
 
localization_priority: Normal
ms.assetid: e3c7ae27-2e54-a174-4fb3-d16093faf759
description: "Contains the information for a single hyperlink associated with a shape. A shape will contain one Hyperlink row for each hyperlink."
---

# Hyperlink Row (Hyperlinks Section)

Contains the information for a single hyperlink associated with a shape. A shape will contain one Hyperlink row for each hyperlink.
  
Hyperlink rows are named Hyperlink. *name*  and contain the following cells. For more details, see the specific cell topics. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[Description](description-cell-hyperlinks-section.md) <br/> |A descriptive text string for a hyperlink.  <br/> |
|[Address](address-cell-hyperlinks-section.md) <br/> |A URL address, MS-DOS file name, or UNC path to which to jump.  <br/> |
|[SubAddress](subaddress-cell-hyperlinks-section.md) <br/> |A location within the target document to link to.  <br/> |
|[ExtraInfo](extrainfo-cell-hyperlinks-section.md) <br/> |A string that passes information to be used in resolving a URL.  <br/> |
|[Frame](frame-cell-hyperlinks-section.md) <br/> |The name of a frame to target when Microsoft Office Visio is open as an Active document in an ActiveX container. The default is an empty string.  <br/> |
|[SortKey](sortkey-cell-hyperlinks-section.md) <br/> |Determines the order of hyperlinks as they appear on the shortcut menu.  <br/> |
|[NewWindow](newwindow-cell-hyperlinks-section.md) <br/> |Specifies whether to open the hyperlink in a new window. If TRUE, opens the linked page, document, or Web site in a new window. The default is FALSE.  <br/> |
|[Default](default-cell-hyperlinks-section.md) <br/> |The default hyperlink for a shape or page.  <br/> |
|[Invisible](invisible-cell-hyperlinks-section.md) <br/> |Indicates whether the hyperlink appears on the shortcut menu.  <br/> |
   
## Remarks

 You can add as many Hyperlink.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add hyperlinks to an existing Hyperlinks section, right-click a row and click **Insert Row** on the shortcut menu. 
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign meaningful names to Hyperlink. *name*  rows, click the row, and then type a name such as  *Marketing*  , for example, to create the row name Hyperlink.Marketing. You can then reference the Description cell using Hyperlink.Marketing.Description. 
  
The row name you enter must be unique within the section.
  

