---
title: "BlockSizeY Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm110
 
ms.localizationpriority: medium
ms.assetid: be51e18e-ea49-0788-1a17-866090afb9f4
description: "Determines the vertical block size, the area in which each of your shapes must fit on the drawing page when you lay out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options)."
---

# BlockSizeY Cell (Page Layout Section)

Determines the vertical block size, the area in which each of your shapes must fit on the drawing page when you lay out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**).
  
## Remarks

You can also set this value in the **Layout and Routing Spacing** dialog box (on the **Design** tab, click the arrow in the **Page Setup** group, click the **Layout and Routing** tab, and then click **Spacing**).
  
To get a reference to the BlockSizeY cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | BlockSizeY  <br/> |
   
To get a reference to the BlockSizeY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPageLayout** <br/> |
| **Cell index:**  <br/> |**visPLOBlockSizeY** <br/> |
   

