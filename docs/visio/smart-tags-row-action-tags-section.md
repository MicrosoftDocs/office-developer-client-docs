---
title: "Smart Tags Row (Action Tags Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1026926
 
localization_priority: Normal
ms.assetid: 065c6977-c737-a4f4-effa-0fd2c98e8bbf
description: "Contains the information for a single action tag associated with a shape or page. A shape or page contains one Smart Tags row for each action tag."
---

# Smart Tags Row (Action Tags Section)

Contains the information for a single action tag associated with a shape or page. A shape or page contains one Smart Tags row for each action tag.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
Smart Tags rows are named SmartTags. *name*  and contain the following cells. For more details, see the specific cell topics. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-action-tags-section.md) <br/> |The  *x*  -coordinate position of a point in the shape's local coordinates around which the action tag button is placed.  <br/> |
|[Y](y-cell-action-tags-section.md) <br/> |The  *y*  -coordinate position of a point in the shape's local coordinates around which the action tag button is placed.  <br/> |
|[TagName](tagname-cell-action-tags-section.md) <br/> |The logical name of the action tag.  <br/> |
|[X Justify](x-justify-cell-action-tags-section.md) <br/> |The  *x*  -offset of the action tag button relative to the point defined by the X and Y cells.  <br/> |
|[Y Justify](y-justify-cell-action-tags-section.md) <br/> |The  *y*  -offset of the action tag button relative to the point defined by the X and Y cells.  <br/> |
|[DisplayMode](displaymode-cell-action-tags-section.md) <br/> |Determines when the action tag will appear.  <br/> |
|[ButtonFace](buttonface-cell-action-tags-section.md) <br/> |The ID of the image that appears on the face of the action tag button.  <br/> |
|[Description](description-cell-action-tags-section.md) <br/> |Descriptive string for the action tag.  <br/> |
|[Disabled](disabled-cell-action-tags-section.md) <br/> |Indicates whether the action tag is disabled.  <br/> |
   
## Remarks

 You can add as many SmartTags.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add an action tag to an existing Smart Tags section, right-click a row and click **Insert Row** on the shortcut menu. 
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign meaningful names to Smart Tags. *name*  rows, click the row, and then type a name such as  *Size*  , for example, to create the row name Smart Tags.Size. You can then reference the Description cell using Smart Tags.Size.Description. 
  
The row name you enter must be unique within the section.
  

