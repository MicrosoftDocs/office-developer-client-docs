---
title: "Spacing Cell (Character Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm955
 
ms.localizationpriority: medium
ms.assetid: 46feb136-01ac-1303-66ab-d772c0ec41a0
description: "Controls the amount of space between two or more characters. Space can be added or subtracted in 1/20th point increments."
---

# Spacing Cell (Character Section)

Controls the amount of space between two or more characters. Space can be added or subtracted in 1/20th point increments.
  
## Remarks

You can also set the value of this cell by using the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the Spacing cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Char.Letterspace[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Spacing cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionCharacter** <br/> |
|**Row index:**  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visCharacterLetterspace** <br/> |
   

