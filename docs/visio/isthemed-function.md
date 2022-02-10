---
title: "ISTHEMED Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 91cde601-dca9-4737-afe1-bdf76638dfe3
description: "Returns a Boolean value indicating whether a shape has a theme applied to it."
---

# ISTHEMED Function

Returns a Boolean value indicating whether a shape has a theme applied to it. 
  
## Version Information

Version Added: Visio 2013 
  
## Syntax

 **ISTHEMED**()
  
## Return value

Boolean
  
## Remarks

> [!NOTE]
> The **ISTHEMED** function in Visio 2013 replaces the **CELLISTHEMED** function from previous versions of Visio. 
  
The **ISTHEMED** function lets you assign appropriate parts of a theme's formatting to a shape but retain the ability to override other parts of the theme formatting with manually-applied formatting. If you subsequently reapply the theme, any manual formatting is overridden and the shape takes on all of the theme's formatting. 
  
 **ISTHEMED** evaluates to TRUE if the [ColorSchemeIndex](colorschemeindex-cell-theme-properties-section.md) cell in the shape is greater than 0. If this cell is equal to 0, then **ISTHEMED** evaluates to FALSE. The theme of the DocumentSheet and PageSheet won't affect the value of the **ISTHEMED** function used in a ShapeSheet. Only if the **ISTHEMED** function shows up in the PageSheet does the page's theme matter. 
  
## Example

||||
|:-----|:-----|:-----|
|Cell  <br/> |Formula  <br/> |Result  <br/> |
|Char.Font  <br/> |IF(ISTHEMED(), THEMEVAL(), FONT("Calibri"))  <br/> |If the shape has a themed applied to it, the shape text accepts the font formatting from the theme. If the shape is not themed, the shape text is formatted with the "Calibri" font. |
|LineColor  <br/> |IF(ISTHEMED, RGB(255, 0, 0), RGB(0, 255, 0))  <br/> |If the shape has a themed applied to it, the shape's line color is red. If the shape is not themed, the shape's line color is green. |
   

