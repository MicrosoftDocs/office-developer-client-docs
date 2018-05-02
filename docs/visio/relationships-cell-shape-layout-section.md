---
title: "Relationships Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm80005
 
localization_priority: Normal
ms.assetid: 4168cd98-9674-1233-254f-0afe81b7245b
description: "Stores the relationships between containers, lists, callouts, and shapes."
---

# Relationships Cell (Shape Layout Section)

Stores the relationships between containers, lists, callouts, and shapes. 
  
## Remarks

 Microsoft Visio uses the Relationships cell to store the relationships that involve this shape. A series of DEPENDSON functions, with the parameters shown, are used to represent relationships with this shape, as shown in the following table. 
  
|**First parameter**|**Additional parameters**|
|:-----|:-----|
|1  <br/> |Shapes that are members of this container.  <br/> |
|2  <br/> |Shapes that are members of this list.  <br/> |
|3  <br/> |Callouts that are associated with this shape.  <br/> |
|4  <br/> |Containers that this shape is a member of.  <br/> |
|5  <br/> |List that this list item is a member of.  <br/> |
|6  <br/> |Shape associated with this callout.  <br/> |
|7  <br/> |Container on the left boundary edge of which this shape sits.  <br/> |
|8  <br/> |Container on the right boundary edge of which this shape sits.  <br/> |
|9  <br/> |Container on the top boundary edge of which this shape sits.  <br/> |
|10  <br/> |Container on the bottom boundary edge of which this shape sits.  <br/> |
|11  <br/> |List that this list overlaps.  <br/> |
   
To get a reference to the Relationships cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Relationships  <br/> |
   
To get a reference to the Relationships cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLORelationships** <br/> |
   

