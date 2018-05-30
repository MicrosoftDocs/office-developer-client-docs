---
title: "ShapePlaceStyle Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm70007
 
localization_priority: Normal
ms.assetid: 29bfe8ec-ca12-8fbf-b62b-ece3710dfe2e
description: "Specifies how shapes are placed on the page when shapes are laid out in the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). Stores layout style and alignment values from VisCellIndices ."
---

# ShapePlaceStyle Cell (Shape Layout Section)

Specifies how shapes are placed on the page when shapes are laid out in the **Configure Layout** dialog box (on the **Design** tab, in the **Layout** group, click **Re-Layout Page**, and then click **More Layout Options**). Stores layout style and alignment values from **VisCellIndices**. 
  
|**Constant**|**Value**|
|:-----|:-----|
|**visLOPlaceBottomToTop** <br/> |4  <br/> |
|**visLOPlaceCircular** <br/> |6  <br/> |
|**visLOPlaceCompactDownLeft** <br/> |14  <br/> |
|**visLOPlaceCompactDownRight** <br/> |7  <br/> |
|**visLOPlaceCompactLeftDown** <br/> |13  <br/> |
|**visLOPlaceCompactLeftUp** <br/> |12  <br/> |
|**visLOPlaceCompactRightDown** <br/> |8  <br/> |
|**visLOPlaceCompactRightUp** <br/> |9  <br/> |
|**visLOPlaceCompactUpLeft** <br/> |11  <br/> |
|**visLOPlaceCompactUpRight** <br/> |10  <br/> |
|**visLOPlaceDefault** <br/> |0  <br/> |
|**visLOPlaceHierarchyBottomToTopCenter** <br/> |20  <br/> |
|**visLOPlaceHierarchyBottomToTopLeft** <br/> |19  <br/> |
|**visLOPlaceHierarchyBottomToTopRight** <br/> |21  <br/> |
|**visLOPlaceHierarchyLeftToRightBottom** <br/> |24  <br/> |
|**visLOPlaceHierarchyLeftToRightMiddle** <br/> |23  <br/> |
|**visLOPlaceHierarchyLeftToRightTop** <br/> |22  <br/> |
|**visLOPlaceHierarchyRightToLeftBottom** <br/> |27  <br/> |
|**visLOPlaceHierarchyRightToLeftMiddle** <br/> |26  <br/> |
|**visLOPlaceHierarchyRightToLeftTop** <br/> |25  <br/> |
|**visLOPlaceHierarchyTopToBottomCenter** <br/> |17  <br/> |
|**visLOPlaceHierarchyTopToBottomLeft** <br/> |16  <br/> |
|**visLOPlaceHierarchyTopToBottomRight** <br/> |18  <br/> |
|**visLOPlaceLeftToRight** <br/> |2  <br/> |
|**visLOPlaceParentDefault** <br/> |15  <br/> |
|**visLOPlaceRadial** <br/> |3  <br/> |
|**visLOPlaceRightToLeft** <br/> |5  <br/> |
|**visLOPlaceTopToBottom** <br/> |1  <br/> |
   
To refer to the ShapePlaceStyle cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapePlaceStyle  <br/> |
   
To refer to the ShapePlaceStyle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOPlaceStyle** <br/> |
   

