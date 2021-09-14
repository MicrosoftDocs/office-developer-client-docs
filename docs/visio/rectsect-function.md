---
title: "RECTSECT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251486
 
ms.localizationpriority: medium
ms.assetid: e83343c5-df5f-bf74-f854-6380176693a2
description: "Calculates the sector of a rectangle associated with x and y and returns an integer 0 to 4, indicating the sector."
---

# RECTSECT Function

Calculates the sector of a rectangle associated with  *x*  and  *y*  and returns an integer 0 to 4, indicating the sector. 
  
## Syntax

RECTSECT(***width***, ***height***, ***x***, ***y***, ***option*** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _width_ <br/> |Required  <br/> |**String** <br/> |Width of the rectangle.  <br/> |
| _height_ <br/> |Required  <br/> |**String** <br/> |Height of the rectangle.  <br/> |
| _x_ <br/> |Required  <br/> |**String** <br/> |An x-coordinate.  <br/> |
| _y_ <br/> |Required  <br/> |**String** <br/> |A y-coordinate.  <br/> |
| _option_ <br/> |Required  <br/> |**Boolean** <br/> |Specifies how points that fall on the diagonals are treated. Set the value to 0 to use the left and right sectors for points on a diagonal. Set the value to 1 to use the top and bottom sectors for points on a diagonal.  <br/> |
   
## Remarks

Consider a rectangle that has a  *width*  and a  *height*  , and a point (*x,y*) from the center point of the rectangle. Draw diagonal lines through the corners of the rectangle to divide it into four sectors and a center point. The sectors 0 through 4 represent the center-point, right, top, left, and bottom respectively. 
  
![Sectors 0 through 4 represent the center-point, right, top, left, and bottom respectively](media/ShpSheetRef_CA_03_ZA07645862.gif)
  
## Example

RECTSECT(1 in, 2 in, 1 in, -7 in, 0) 
  
Returns 4. 
  

