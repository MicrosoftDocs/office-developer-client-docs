---
title: "Rounding Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm860
 
localization_priority: Normal
ms.assetid: c44457ca-997a-5315-44dd-4218e4203550
description: "Indicates the radius of the rounding arc applied where two contiguous segments of a path meet. For example, rounding can be used to give a rectangle rounded corners. To set rounding, enter a value with units of measure (a number-unit pair)."
---

# Rounding Cell (Line Format Section)

Indicates the radius of the rounding arc applied where two contiguous segments of a path meet. For example, rounding can be used to give a rectangle rounded corners. To set rounding, enter a value with units of measure (a number-unit pair).
  
## Remarks

You can also set this value in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Weight**, and then click **More Lines**).
  
To get a reference to the Rounding cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Rounding  <br/> |
   
To get a reference to the Rounding cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLine** <br/> |
|Cell index:  <br/> |**visLineRounding** <br/> |
   

