---
title: "Bullet Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm130
 
ms.localizationpriority: medium
ms.assetid: 124a5ee1-6dd1-d17d-6f0e-dbaa5d95d9cd

description: "Determines the bullet style."
---

# Bullet Cell (Paragraph Section)

Determines the bullet style.
  
|**Value**|**Bullet style**|
|:-----|:-----|
|0   |None  <br/> |
|1   |![round bullet](media/IC_Bullet1_ZA07645847.gif) |
|2   |![diamond bullet](media/IC_Bullet2_ZA07645848.gif) |
|3   |![square bullet](media/IC_Bullet3_ZA07645849.gif) |
|4   |![check box bullet](media/IC_Bullet4_ZA07645851.gif) |
|5   |![four diamond bullet](media/IC_Bullet5_ZA07645852.gif) |
|6   |![procedure arrow bullet](media/IC_Bullet6_ZA07645853.gif) |
|7   |![checkmark bullet](media/IC_Bullet7_ZA07645854.gif) |

 
## Remarks

To set the value of this cell, right-click a shape, point to **Format**, click **Text**, and then click the **Bullets** tab. 
  
To get a reference to the BulletString cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name: |Para.Bullet[ *i*  ] where *i*  = <1>, 2, 3, ... |

To get a reference to the Bullet cell by index from a program, use the **CellsSRC** property with the following arguments: 
|||
|:-----|:-----|
|Section index: |**visSectionParagraph** |
|Row index:  |**visRowParagraph** +  *i* where  *i*  = 0, 1, 2, ... |
|Cell index: |**visBulletIndex** |
