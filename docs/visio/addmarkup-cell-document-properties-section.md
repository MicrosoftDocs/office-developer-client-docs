---
title: "AddMarkup Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1030801
 
ms.localizationpriority: medium
ms.assetid: 46146424-b4c9-2240-36c0-19bb35ec51d1
description: "Indicates whether the document is being reviewed for markup."
---

# AddMarkup Cell (Document Properties Section)

Indicates whether the document is being reviewed for markup.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Document is being reviewed. |
|FALSE  <br/> |Document is not being reviewed (the default). |
   
## Remarks

When the AddMarkup cell is set to TRUE, the reviewer is adding markup and changes are applied to markup overlay pages, not to original drawing pages. When the AddMarkup cell is FALSE, markup tracking is off and changes are applied to the original drawing pages.
  
> [!NOTE]
> You can prevent markup on your documents by using the GUARD function. If the AddMarkup cell contains the formula =GUARD(FALSE), the **Track Markup** command is disabled. 
  
This setting corresponds to the **Track Markup** command setting in the **Markup** group on the **Review** tab. 
  
To get a reference to the AddMarkup cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |AddMarkup  <br/> |
   
To get a reference to the AddMarkup cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowDoc** <br/> |
|Cell index:  <br/> |**visDocAddMarkup** <br/> |
   

