---
title: "Ask Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60
 
ms.localizationpriority: medium
ms.assetid: b499a5eb-db8f-ebd0-d505-c9a002205e7d

description: "Determines whether a user is queried to enter shape data for a shape when an instance is created or the shape is duplicated or copied."
---

# Ask Cell (Shape Data Section)

Determines whether a user is queried to enter shape data for a shape when an instance is created or the shape is duplicated or copied.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Ask user to enter shape data in the **Define Shape Data** dialog box. |
|FALSE  <br/> |Do not ask user to enter data. |
   
## Remarks

The value in this cell corresponds to the **Ask on drop** check box in the **Define Shape Data** dialog box (right-click the shape, point to **Data**, and then click **Define Shape Data**).
  
To get a reference to the Ask cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Prop. *name*  .Verify            where Prop.  *name*  is the name of the custom property row. |
   
To get a reference to the Ask cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionProp** <br/> |
|Row index:  <br/> |**visRowProp** +  *i*            where  *i*  = 0, 1, 2,... |
|Cell index:  <br/> |**visCustPropsAsk** <br/> |
   

