---
title: "About Error Values"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251832
 
localization_priority: Normal
ms.assetid: 56430658-a798-c004-b4ba-363443f43ded
description: "Error values are displayed in cells that have incorrect formulas for that cell."
---

# About Error Values

Error values are displayed in cells that have incorrect formulas for that cell.
  
If a formula references a cell that contains an error value, that formula also displays an error value. You can use the function ISERR, ISERRNA, ISERROR, or ISERRVALUE to look for error values.
  
**Error values**

||||
|:-----|:-----|:-----|
|**If the cell displays** <br/> |**The formula includes** <br/> |**Example** <br/> |
| #DIV/0!  <br/> |Division by 0  <br/> |10/0  <br/> |
| #VALUE!  <br/> | An argument or operand of the wrong type  <br/> | 5 + "House"  <br/> |
| #REF!  <br/> | A reference to a cell that does not exist  <br/> | A cell that refers to another cell that no longer exists  <br/> |
| #NUM!  <br/> | An invalid number  <br/> | Square root of a negative number  <br/> |
| #N/A!  <br/> | Not an available value  <br/> | NA( ) function  <br/> |
| #DIM!  <br/> | A dimensional value that exceeds the dimension range (valid powers are integers -128 \<= n \<= 127)  <br/> A dimensional value used with an inappropriate operation  <br/> |1in^100 \* 1in^100 (the result is 1in^200, which is beyond the dimension range)  <br/> 5.2cm^1.5 (not an integer power)  <br/> |
   

