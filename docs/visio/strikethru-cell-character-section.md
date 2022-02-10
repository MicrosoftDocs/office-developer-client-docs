---
title: "Strikethru Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm975
 
ms.localizationpriority: medium
ms.assetid: b03b4415-0b1a-eb03-2b5e-373b39a0f07a
description: "Determines whether the text is formatted as strikethrough."
---

# Strikethru Cell (Character Section)

Determines whether the text is formatted as strikethrough.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text is formatted as strikethrough. |
|FALSE  <br/> |Text is not formatted as strikethrough. |
   
## Remarks

You can also set the value of this cell by using the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the Strikethru cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.Strikethru[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Strikethru cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visCharacterStrikethru** <br/> |
   

