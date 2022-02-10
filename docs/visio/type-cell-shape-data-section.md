---
title: "Type Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1055
 
ms.localizationpriority: medium
ms.assetid: 1e24a906-83ce-32d2-5d7b-ba6dd6eea2d3
description: "Specifies a data type for the shape data value."
---

# Type Cell (Shape Data Section)

Specifies a data type for the shape data value.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |String. This is the default. |**visPropTypeString** <br/> |
|1  <br/> |Fixed list. Displays the list items in a drop-down combo box in the **Define Shape Data** dialog box. Specify the list items in the Format cell. Users can select only one item from the list. |**visPropTypeListFix** <br/> |
|2  <br/> |Number. Includes date, time, duration, and currency values as well as scalars, dimensions, and angles. Specify a format picture in the Format cell. |**visPropTypeNumber** <br/> |
|3  <br/> |Boolean. Displays FALSE and TRUE as items users can select from a drop-down list box in the **Define Shape Data** dialog box. |**visPropTypeBool** <br/> |
|4  <br/> |Variable list. Displays the list items in a drop-down combo box in the **Define Shape Data** dialog box. Specify the list items in the Format cell. Users can select a list item or enter a new item that is added to the current list in the Format cell. |**visPropTypeListVar** <br/> |
|5  <br/> |Date or time value. Displays days, months, and years, or seconds, minutes, and hours, or a combined date and time value. Specify a format picture in the Format cell. |**visPropTypeDate** <br/> |
|6  <br/> |Duration value. Displays elapsed time. Specify a format picture in the Format cell. |**visPropTypeDuration** <br/> |
|7  <br/> |Currency value. Uses the system's current Regional Settings. Specify a format picture in the Format cell. |**visPropTypeCurrency** <br/> |
   
## Remarks

To get a reference to the Type cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Prop. *Name*  .Type where Prop.  *Name*  is the row name  <br/> |
   
To get a reference to the Type cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionProp** <br/> |
|Row index:  <br/> |**visRowProp** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visCustPropsType** <br/> |
   

