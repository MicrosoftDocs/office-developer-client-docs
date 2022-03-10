---
title: "Font Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm390
 
ms.localizationpriority: medium
ms.assetid: 935760a9-307e-90bc-c301-d04283d97427

description: "Represents the number of the font used to format the text. Font numbers vary according to the fonts installed on your system. The number 0 represents the default font, which is typically Arial."
---

# Font Cell (Character Section)

Represents the number of the font used to format the text. Font numbers vary according to the fonts installed on your system. The number 0 represents the default font, which is typically Arial.
  
## Remarks

To get a reference to the Font cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Char.Font[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Font cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionCharacter** <br/> |
| **Row index:**  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visCharacterFont** <br/> |
   

