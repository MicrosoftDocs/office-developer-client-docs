---
title: "AvenueSizeX Cell (Page Layout Section)" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm65
 
ms.localizationpriority: medium
ms.assetid: 86fe25ed-590d-b2f0-5dfe-9746a19c6b04
description: "Determines the amount of horizontal space between shapes on the drawing page when you lay out shapes by using the Configure Layout dialog box."
---

# AvenueSizeX Cell (Page Layout Section)

Determines the amount of horizontal space between shapes on the drawing page when you lay out shapes by using the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**).
  
## Remarks

You can also set this value in the **Layout and Routing Spacing** dialog box (on the **Design** tab, click the arrow in the **Page Setup** group, click the **Layout and Routing** tab, and then click **Spacing**).
  
The dynamic grid uses the setting in the AvenueSizeX cell when only one shape is available for calculating horizontal spacing. To use the dynamic grid, on the **View** tab, in the **Visual Aids** group, select **Dynamic Grid**.
  
To get a reference to the AvenueSizeX cell by name from another formula, or from a program by using the **CellsU** property, use:
  
|**Value**|**Description**|
|:-----|:-----|
| Cell name:  <br/> | AvenueSizeY  <br/> |

To get a reference to the AvenueSizeX cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description**|
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOAvenueSizeX** <br/> |
