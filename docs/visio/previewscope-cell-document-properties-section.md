---
title: "PreviewScope Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm820
 
ms.localizationpriority: medium
ms.assetid: d03ae1b3-da6c-56d3-4f96-6e131c04e93e
description: "Determines whether your drawing includes a preview. If your drawing does include a preview, it determines whether the preview shows the first page only or all of the pages in the drawing."
---

# PreviewScope Cell (Document Properties Section)

Determines whether your drawing includes a preview. If your drawing does include a preview, it determines whether the preview shows the first page only or all of the pages in the drawing.
  
|**Value**|**Preview scope**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | First page  <br/> |**visDocPreviewScope1stPage** <br/> |
| 1  <br/> | None  <br/> |**visDocPreviewScopeNone** <br/> |
| 2  <br/> | All pages  <br/> |**visDocPreviewScopeAllPages** <br/> |
   
## Remarks

You can also set this value on the **Summary** tab in the **Properties** dialog box (click the **Office** button, click the **Info** tab, click **Document Properties**, and then click **Advanced Properties**).
  
To get a reference to the PreviewScope cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PreviewScope  <br/> |
   
To get a reference to the PreviewScope cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowDoc** <br/> |
| Cell index:  <br/> |**visDocPreviewScope** <br/> |
   

