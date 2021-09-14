---
title: "SortKey Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251345
 
ms.localizationpriority: medium
ms.assetid: 67fa5389-f0b9-a9db-8d19-9b16e256dfa3
description: "Evaluates to a string that influences the order in which items in the Shape Data window are listed."
---

# SortKey Cell (Shape Data Section)

Evaluates to a string that influences the order in which items in the **Shape Data** window are listed. 
  
## Remarks

The calculation used to compare SortKey values is locale-specific and case insensitive. If SortKey values are equal, the shape data is listed in row order. Shape data that have no sort key are listed after shape data that contain a sort key.
  
Following is an example of using sort keys to display the shape data in the **Shape Data** window in the order: Item Number, Quantity, Price. 
  
 *Row, Label,*  and  *SortKey*  refer to cells in the shape data row. In this case, the shape data rows have been named. 
  
|**Row**|**Label**|**SortKey**|
|:-----|:-----|:-----|
| Prop.Item  <br/> | Item Number  <br/> | 1  <br/> |
| Prop.Price  <br/> | Price  <br/> | 3  <br/> |
| Prop.Quan  <br/> | Quantity  <br/> | 2  <br/> |
   
To get a reference to the SortKey cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Prop.  *Name*  .SortKey where Prop.  *Name*  is the name of the custom property row  <br/> |
   
To get a reference to the SortKey cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionProp** <br/> |
| Row index:  <br/> |**visRowProp** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCustPropsSortKey** <br/> |
   

