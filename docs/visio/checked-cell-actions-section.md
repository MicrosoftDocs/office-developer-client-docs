---
title: "Checked Cell (Actions Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm155
 
ms.localizationpriority: medium
ms.assetid: 50937e29-eaa1-0cd0-53cc-dc17e7793e55

description: "Indicates whether an item is checked on the shortcut or action tag menu."
---

# Checked Cell (Actions Section)

Indicates whether an item is checked on the shortcut or action tag menu.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Check mark is displayed. |
|FALSE  <br/> |Check mark is not displayed (the default). |

## Remarks

To get a reference to the Checked cell by name from another formula, or from a program by using the **CellsU** property, use:
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Actions. *name*  .Checked           where Actions. *name* is the name of the Actions row  <br/> |

To get a reference to the Checked cell by index from a program, use the **CellsSRC** property with the following arguments:
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionAction** <br/> |
|**Row index:**  <br/> |**visRowAction** +  *i*           where  *i*  = 0, 1, 2, ... |
|**Cell index:**  <br/> |**visActionChecked** <br/> |
