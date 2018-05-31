---
title: "Bullet Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm130
 
localization_priority: Normal
ms.assetid: 124a5ee1-6dd1-d17d-6f0e-dbaa5d95d9cd

description: "Determines the bullet style."
---

# Bullet Cell (Paragraph Section)

Determines the bullet style.
  
|**Value**|**Bullet style**|
|:-----|:-----|
|0  <br/> |None  <br/> |
|1  <br/> |![](media/IC_Bullet1_ZA07645847.gif)           <br/> |
|2  <br/> |![](media/IC_Bullet2_ZA07645848.gif)           <br/> |
|3  <br/> |![](media/IC_Bullet3_ZA07645849.gif)           <br/> |
|4  <br/> |![](media/IC_Bullet4_ZA07645851.gif)           <br/> |
|5  <br/> |![](media/IC_Bullet5_ZA07645852.gif)           <br/> |
|6  <br/> |![](media/IC_Bullet6_ZA07645853.gif)           <br/> |
|7  <br/> |![](media/IC_Bullet7_ZA07645854.gif)           <br/> |
   
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionParagraph** <br/> |
|Row index:  <br/> |**visRowParagraph** +  *i*           where  *i*  = 0, 1, 2, ...  <br/> |
|Cell index:  <br/> |**visBulletIndex** <br/> |
   
## Remarks

You can also set the value of this cell by right-clicking a shape, pointing to **Format**, clicking **Text**, and then clicking the **Bullets** tab. 
  
To get a reference to the Bullet cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Para.Bullet[ *i*  ]           where  *i*  = <1>, 2, 3, ...  <br/> |
   
To get a reference to the Bullet cell by index from a program, use the **CellsSRC** property with the following arguments: 
  

