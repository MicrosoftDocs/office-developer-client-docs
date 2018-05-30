---
title: "DoubleULine Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm260
 
localization_priority: Normal
ms.assetid: c18955c8-d653-c29d-d3da-9d3cd0241e17

description: "Determines whether the range of text has a double underline below it."
---

# DoubleULine Cell (Character Section)

Determines whether the range of text has a double underline below it.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text has a double underline below it.  <br/> |
|FALSE  <br/> |Text does not have a double underline below it.  <br/> |
   
## Remarks

The DoubleULine cell contains formatting information applied to a sub-range of a shape's text if the Characters section contains multiple rows. Otherwise, it contains formatting information for all of the shape's text.
  
You can also set the value of this cell by using the **Text** dialog box (click the **Font** arrow on the **Home** tab). 
  
To get a reference to the DoubleULine cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Char.DblUnderline[ *i*  ]           where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the DoubleULine cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionCharacter** <br/> |
|Row index:  <br/> |**visRowCharacter** +  *i*           where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visCharacterDblUnderline** <br/> |
   

