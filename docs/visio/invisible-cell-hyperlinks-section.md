---
title: "Invisible Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033755
 
ms.localizationpriority: medium
ms.assetid: e67dcd83-4a88-a0f8-5c6a-dae51424edbd
description: "Indicates whether a hyperlink appears on the shortcut menu for a shape or page."
---

# Invisible Cell (Hyperlinks Section)

Indicates whether a hyperlink appears on the shortcut menu for a shape or page. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The hyperlink does not appear as a menu item on the shortcut menu.  <br/> |
|FALSE  <br/> |The hyperlink does appear as a menu item on the shortcut menu (the default).  <br/> |
   
## Remarks

To get a reference to the Invisible cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Hyperlink. *name*  .Invisible where Hyperlink  *.name*  is the row name  <br/> |
   
To get a reference to the Invisible cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionHyperlink** <br/> |
|Row index:  <br/> |**visRow1stHyperlink** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visHLinkInvisible** <br/> |
   

