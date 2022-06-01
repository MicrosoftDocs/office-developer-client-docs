---
title: "ScaleX Cell (Print Properties Section)"
description: "ScaleX Cell (Print Properties Section) specifies the percentage of magnification of the drawing page on the printer page."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60072
ms.localizationpriority: medium
ms.assetid: 5916eadc-37f8-47af-fe54-f6062aea318f
---

# ScaleX Cell (Print Properties Section)

Specifies the percentage of magnification of the drawing page on the printer page.
  
## Remarks

This value is used only when the OnPage cell value is FALSE. The ScaleX and ScaleY cells always have the same value, which corresponds to the value in the **Adjust to** setting on the **Print Setup** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). 
  
To get a reference to the ScaleX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ScaleX  <br/> |
   
To get a reference to the ScaleX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPrintProperties** <br/> |
|**Cell index:**  <br/> |**visPrintPropertiesScaleX** <br/> |
   

