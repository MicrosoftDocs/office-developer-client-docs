---
title: "Overline Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251728
 
localization_priority: Normal
ms.assetid: 102cce17-43ee-e313-3412-a72d6ee18fe6
description: "Determines whether the text has a line above it."
---

# Overline Cell (Character Section)

Determines whether the text has a line above it.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text has a line above it.  <br/> |
|FALSE  <br/> |Text does not have a line above it.  <br/> |
   
## Remarks

You can also set the value of this cell by using the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the Overline cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.Overline[ *i*  ] where  *i*  = <1>, 2. 3...  <br/> |
   
To get a reference to the Overline cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visCharacterOverline** <br/> |
   

