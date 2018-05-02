---
title: "ButtonFace Cell (Actions Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60025
 
localization_priority: Normal
ms.assetid: cf15b879-a47e-a5a5-bfdd-1d7ea423742f

description: "Identifies the icon that appears next to an item on a shortcut or action tag menu."
---

# ButtonFace Cell (Actions Section)

Identifies the icon that appears next to an item on a shortcut or action tag menu.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

The string contained in the ButtonFace cell represents the ID of a Microsoft Office button face image. A value of zero (0) or blank means no icon appears. 
  
The IDs that can be used in the ButtonFace cell are the same as the IDs used with the **FaceID** property of a **CommandBarButton** object. For more details about these IDs, search for "working with command bar button images" on MSDN. 
  
To get a reference to the ButtonFace cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |**Actions**.  *name*  . **ButtonFace**         where **Actions**.  *name*  is the name of the actions row  <br/> |
   
To get a reference to the ButtonFace cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*           where **i** = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visActionButtonFace** <br/> |
   

