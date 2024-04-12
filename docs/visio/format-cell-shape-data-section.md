---
title: "Format Cell (Shape Data Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251340
 
ms.localizationpriority: medium
ms.assetid: c36fc895-5577-59f6-0ff5-5892ca81a58f

description: "Specifies the formatting of a shape data item that is a string, a fixed list, a number, a variable list, a date or time, a duration, or a currency."
---

# Format Cell (Shape Data Section)

Specifies the formatting of a shape data item that is a string, a fixed list, a number, a variable list, a date or time, a duration, or a currency.
  
## Remarks

|**Shape data item type**|**Value**|**Format cell contents**|
|:-----|:-----|:-----|
| String  <br/> | 0  <br/> | A format picture appropriate for the data type. |
| Fixed list  <br/> | 1  <br/> | The items to appear in the list, separated by semicolons. |
| Number  <br/> | 2  <br/> | A format picture appropriate for the data type. |
| Variable list  <br/> | 4  <br/> | The items to appear in the list, separated by semicolons. |
| Date or time  <br/> | 5  <br/> | A format picture appropriate for the data type. |
| Duration  <br/> | 6  <br/> | A format picture appropriate for the data type. |
| Currency  <br/> | 7  <br/> | A format picture appropriate for the data type. |
   
As an example of specifying a format picture appropriate for the data type, the format picture "# #/4 UU" formats the number 12.43 in. as 12 2/4 INCHES. For more information about specifying a format picture, see [About format pictures](about-format-pictures.md).
  
An example of specifying items for a list is "Engineering;Human Resources;Sales;Marketing".
  
Date values (type = 5) are displayed in the short date format. Currency values (type = 7) are displayed using the user's current setting for **Currency** on the **Regional Options** tab in the **Regional and Language Options** item in **Control Panel**.
  
A number (type = 2) can represent a dimension, scalar, angle, date, time, or currency. To ensure that an input number is always evaluated as a date, time, or currency, use the DATETIME or CY function in the Format cell instead of a format picture.
  
To get a reference to the Format cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Prop.  *name*  .Format            where Prop.  *name*  is the row name  <br/> |
   
To get a reference to the Format cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionProp** <br/> |
| **Row index:**  <br/> |**visRowProp** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visCustPropsFormat** <br/> |
   

