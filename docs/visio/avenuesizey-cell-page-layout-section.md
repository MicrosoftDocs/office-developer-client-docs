---
title: "AvenueSizeY Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm70
 
ms.localizationpriority: medium
ms.assetid: 9ff2893c-afe5-505e-0b55-48ec1de08a5f
description: "Determines the amount of vertical space between shapes on the drawing page when you lay out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options)."
---

# AvenueSizeY Cell (Page Layout Section)

Determines the amount of vertical space between shapes on the drawing page when you lay out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout** Page, and then click **More Layout Options**).
  
## Remarks

You can also set this value in the **Layout and Routing Spacing** dialog box (on the **Design** tab, click the arrow in the **Page Setup** group, click the **Layout and Routing** tab, and then click **Spacing**).
  
The dynamic grid uses the setting in the AvenueSizeY cell when only one shape is available for calculating vertical spacing. To use the dynamic grid, on the **View** tab, in the **Visual Aids** group, select **Dynamic Grid**.
  
To get a reference to the AvenueSizeY cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | AvenueSizeY  <br/> |
   
To get a reference to the AvenueSizeY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOAvenueSizeY** <br/> |
   

