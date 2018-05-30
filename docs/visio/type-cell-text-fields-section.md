---
title: "Type Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1060
 
localization_priority: Normal
ms.assetid: 69d64520-9a47-07ca-09c7-d1e5da620348
description: "Specifies a data type for the text field value."
---

# Type Cell (Text Fields Section)

Specifies a data type for the text field value.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |String.  <br/> |
|2  <br/> |Number. Includes date, time, duration, and currency values as well as scalars, dimensions, and angles. Specify a format picture in the Format cell.  <br/> |
|5  <br/> |Date or time value. Displays days, months, and years, or seconds, minutes, and hours, or a combined date and time value. Specify a format picture in the Format cell.  <br/> |
|6  <br/> |Duration value. Displays elapsed time. Specify a format picture in the Format cell.  <br/> |
|7  <br/> |Currency value. Uses the system's current Regional Settings. Specify a format picture in the Format cell.  <br/> |
   
## Remarks

You can also set the value of this cell using the **Field** dialog box (with a shape selected, on the **Insert** tab, in the **Text** group, click **Field** ). 
  
To get a reference to the Type cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Fields.Type[ *i*  ] where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the Type cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionTextField** <br/> |
|Row index:  <br/> |**visRowField** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visFieldType** <br/> |
   

