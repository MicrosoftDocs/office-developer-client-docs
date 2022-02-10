---
title: "Scale Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm870
 
ms.localizationpriority: medium
ms.assetid: d6fe2574-b719-f38e-b1f1-592a812f1682
description: "Controls the font width. The default value for this cell is 100%."
---

# Scale Cell (Character Section)

Controls the font width. The default value for this cell is 100%.
  
## Remarks

Set the percentage between 1% and 99% to decrease the font width. Set it between 101% and 600% to increase the font width.
  
You can also set the value of this cell by using the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the Scale cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.FontScale[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Scale cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visCharacterFontScale** <br/> |
   

