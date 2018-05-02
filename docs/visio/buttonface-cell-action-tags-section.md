---
title: "ButtonFace Cell (Action Tags Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60026
 
localization_priority: Normal
ms.assetid: 26f370e1-5193-f47d-7b60-3597975be650

description: "Contains the ID of the button face image that appears on the action tag button."
---

# ButtonFace Cell (Action Tags Section)

Contains the ID of the button face image that appears on the action tag button. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

The string contained in the ButtonFace cell represents the ID of a Microsoft Office button face image. A value of 0 (zero) or blank defaults to the standard action tag "i" info button ![](media/InfoPS_ZA10180114.gif).
  
The IDs that can be used in the ButtonFace cell are the same as the IDs used with the **FaceID** property of a **CommandBarButton** object. For more details about these IDs, search for "working with command bar button images" on MSDN. 
  
To get a reference to the ButtonFace cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SmartTags.  *name*  .ButtonFace           where SmartTags. *name*  is the name of the action tag row  <br/> |
   
To get a reference to the ButtonFace cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionSmartTag** <br/> |
| Row index:  <br/> |**visRowSmartTag** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSmartTagButtonFace** <br/> |
   

