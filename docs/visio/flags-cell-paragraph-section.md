---
title: "Flags Cell (Paragraph Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033782
 
ms.localizationpriority: medium
ms.assetid: 898bf89d-d00f-9769-a89d-787ef708eca5
description: "Indicates whether the text direction is left to right or right to left."
---

# Flags Cell (Paragraph Section)

Indicates whether the text direction is left to right or right to left.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |The text direction is left to right (the default). |
|1  <br/> |The text direction is right to left. |
   
## Remarks

The value in this cell corresponds to the **Direction** setting on the **Paragraph** tab in the **Text** dialog box (on the **Home** tab, click the **Font** arrow), which appears only if a language that uses complex scripts text has been added in the **Microsoft Office Language Preferences** dialog box. (Click **Start**, click **All Programs**, click **Microsoft Office**, click **Microsoft Office Tools**, and then click **Microsoft Office Language Preferences**.) 
  
To get a reference to the Flags cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Para.Flags[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Flags cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionParagraph** <br/> |
|**Row index:**  <br/> |**visRowParagraph** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visFlags** <br/> |
   

