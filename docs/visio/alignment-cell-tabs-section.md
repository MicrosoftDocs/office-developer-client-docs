---
title: "Alignment Cell (Tabs Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm35
 
ms.localizationpriority: medium
ms.assetid: 84234177-a2df-6acc-2761-230bc5d12627
description: "Specifies the tab alignment."
---

# Alignment Cell (Tabs Section)

Specifies the tab alignment.
  
|**Value**|**Alignment**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Left  <br/> |**visTabStopLeft** <br/> |
| 1  <br/> | Center  <br/> |**visTabStopCenter** <br/> |
| 2  <br/> | Right  <br/> |**visTabStopRight** <br/> |
| 3  <br/> | Decimal  <br/> |**visTabStopDecimal** <br/> |
| 4  <br/> | Comma  <br/> |**visTabStopComma** <br/> |
   
## Remarks

To get a reference to the Alignment cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Tabs.  *ij*            where  *i and j =*  <1>, 2, 3  <br/> |
   
To get a reference to the Alignment cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTab** <br/> |
| Row index:  <br/> |**visRowTab +** *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> | (*j*  *3) **+ visTabAlign** <br/> |
   

