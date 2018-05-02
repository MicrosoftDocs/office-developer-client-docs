---
title: "PrintGrid Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033794
 
localization_priority: Normal
ms.assetid: 0504ff7f-2274-7ae3-1f4b-a3d890dbd79a
description: "Specifies whether to print the grid when printing a document page."
---

# PrintGrid Cell (Print Properties Section)

Specifies whether to print the grid when printing a document page.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Show the grid when printing this page.  <br/> |
|FALSE  <br/> |Do not show the grid when printing this page (the default).  <br/> |
   
## Remarks

This value corresponds to the **Gridlines** check box on the **Print Setup** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). Other than color (the printed version is gray), the printed grid is identical to the grid you see in the Microsoft Visio drawing window. 
  
You can choose whether to print the grid on a page-by-page basis. The style of grid can also be defined on a page-by-page basis in the **Ruler &amp; Grid** dialog box (on the **View** tab, click the **Show** arrow) when a page is active. 
  
To get a reference to the PrintGrid cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |PrintGrid  <br/> |
   
To get a reference to the PrintGrid cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPrintProperties** <br/> |
|Cell index:  <br/> |**visPrintPropertiesPrintGrid** <br/> |
   

