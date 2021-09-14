---
title: "ScaleY Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033788
 
ms.localizationpriority: medium
ms.assetid: 02835aff-455b-ffeb-d53b-28387b6ce361
description: "Specifies the percentage of magnification of the drawing page on the printer page."
---

# ScaleY Cell (Print Properties Section)

Specifies the percentage of magnification of the drawing page on the printer page.
  
## Remarks

This value is used only when the OnPage cell value is FALSE. The ScaleX and ScaleY cells always have the same value, which corresponds to the value in the **Adjust to** setting on the **Print Setup** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). 
  
To get a reference to the ScaleY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ScaleY  <br/> |
   
To get a reference to the ScaleY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPrintProperties** <br/> |
|Cell index:  <br/> |**visPrintPropertiesScaleY** <br/> |
   

