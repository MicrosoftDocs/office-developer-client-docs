---
title: "VerticalAlign Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1105
 
ms.localizationpriority: medium
ms.assetid: ff34a23b-2881-864f-42e4-871c4fde0992
description: "Determines the vertical alignment of text within the text block."
---

# VerticalAlign Cell (Text Block Format Section)

Determines the vertical alignment of text within the text block.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Top  <br/> |**visVertTop** <br/> |
| 1  <br/> | Middle  <br/> |**visVertMiddle** <br/> |
| 2  <br/> | Bottom  <br/> |**visVertBottom** <br/> |
   
## Remarks

To get a reference to the VerticalAlign cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | VerticalAlign  <br/> |
   
To get a reference to the VerticalAlign cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowText** <br/> |
| Cell index:  <br/> |**visTxtBlkVerticalAlign** <br/> |
   

