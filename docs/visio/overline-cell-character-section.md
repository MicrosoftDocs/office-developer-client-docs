---
title: "Overline Cell (Character Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251728
 
ms.localizationpriority: medium
ms.assetid: 102cce17-43ee-e313-3412-a72d6ee18fe6
description: "Determines whether the text has a line above it."
---

# Overline Cell (Character Section)

Determines whether the text has a line above it.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text has a line above it. |
|FALSE  <br/> |Text does not have a line above it. |
   
## Remarks

You can also set the value of this cell by using the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the Overline cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Char.Overline[ *i*  ] where  *i*  = <1>, 2. 3... |
   
To get a reference to the Overline cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionCharacter** <br/> |
|**Row index:**  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visCharacterOverline** <br/> |
   

