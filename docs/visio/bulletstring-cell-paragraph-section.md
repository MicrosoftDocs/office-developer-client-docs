---
title: "BulletString Cell (Paragraph Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm135
 
ms.localizationpriority: medium
ms.assetid: 38285824-30ad-0cf2-07cb-0103ab3a415a

description: "Allows you to create a custom bullet style."
---

# BulletString Cell (Paragraph Section)

Allows you to create a custom bullet style. 
  
## Remarks

Enter the style as a string (within quotation marks). For example, you could enter the string, "ooo."
  
You can also set the value of this cell by right-clicking a shape, pointing to **Format**, clicking **Text**, and then clicking the **Bullets** tab. 
  
To get a reference to the BulletString cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Para.BulletStr[ *i*  ]           where  *i*  = <1>, 2, 3, ... |
   
To get a reference to the BulletString cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionParagraph** <br/> |
|**Row index:**  <br/> |**visRowParagraph** +  *i*           where  *i*  = 0, 1, 2, ... |
|**Cell index:**  <br/> |**visBulletString** <br/> |
   

