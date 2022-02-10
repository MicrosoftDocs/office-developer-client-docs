---
title: "Format Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm400
 
ms.localizationpriority: medium
ms.assetid: ab937a00-84c2-6c1c-9080-b7c95ead4f63

description: "Specifies the formatting of a text field that is a string, a number, a date or time, a duration, or a currency."
---

# Format Cell (Text Fields Section)

Specifies the formatting of a text field that is a string, a number, a date or time, a duration, or a currency.
  
## Remarks

If the value of the Type cell is 0, 2, 5, 6, or 7 (string, number, date or time, duration, or currency, respectively), specify a format picture appropriate for the data type. For example, the format picture "# #/4 UU" formats the number 12.43 in. as 12 2/4 INCHES. For more information about specifying a format picture, see [About format pictures](about-format-pictures.md).
  
A number (Type = 2) can represent a dimension, scalar, angle, date, time, or currency. To ensure that an input number is always evaluated as a date, time, or currency, use the DATETIME or CY function in the Format cell instead of a format picture.
  
To get a reference to the Format cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Fields.Format[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Format cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTextField** <br/> |
| Row index:  <br/> |**visRowField** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visFieldFormat** <br/> |
   

