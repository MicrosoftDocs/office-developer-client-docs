---
title: "DocLockReplace Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 74eae5e5-80ab-4e10-b292-e58a6d7607d2
description: "Determines whether the replace shape UI should be disabled for this document."
---

# DocLockReplace Cell (Document Properties Section)

Determines whether the replace shape UI should be disabled for this document.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **Replace Shape** button is grayed out in the UI. |
|FALSE  <br/> |The **Replace Shape** button is active in the UI. Users can use the Replace Shape feature in this document. |

## Remarks

To get a reference to the **DocLockReplace** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use:
  
|**Value**|**Description** |
|:-----|:-----|
| **Cell name:**  <br/> | DocLocReplace  <br/> |

To get a reference to the **DocLocReplace** cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description** |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowDoc** <br/> |
| **Cell index:**  <br/> |**visDocLockReplace** <br/> |
