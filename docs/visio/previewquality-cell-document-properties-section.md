---
title: "PreviewQuality Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm815
 
ms.localizationpriority: medium
ms.assetid: b7d90666-a1bb-f0de-32da-b2855977f648
description: "Determines whether the drawing preview is draft quality or detailed."
---

# PreviewQuality Cell (Document Properties Section)

Determines whether the drawing preview is draft quality or detailed.
  
|**Value**|**Preview quality**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Draft  <br/> |**visDocPreviewQualityDraft** <br/> |
| 1  <br/> | Detailed  <br/> |**visDocPreviewQualityDetailed** <br/> |
   
## Remarks

You can also set this value on the **Summary** tab in the **Properties** dialog box (click the **Office** button, click the **Info** tab, click **Document Properties**, and then click **Advanced Properties**).
  
To get a reference to the PreviewQuality cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PreviewQuality  <br/> |
   
To get a reference to the PreviewQuality cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowDoc** <br/> |
| Cell index:  <br/> |**visDocPreviewQuality** <br/> |
   

