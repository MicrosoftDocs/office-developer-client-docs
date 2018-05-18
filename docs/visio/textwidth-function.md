---
title: "TEXTWIDTH Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251505
 
localization_priority: Normal
ms.assetid: a9b8efcf-edc0-ad99-deae-21df16c58807
description: "Returns the width of the composed text in a shape."
---

# TEXTWIDTH Function

Returns the width of the composed text in a shape. 
  
## Syntax

TEXTWIDTH( ** *shapename!TheText* ** ** *[,maximumwidth]* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _shapename!theText_ <br/> |Required  <br/> |**String** <br/> |A reference to the cell named TheText in the target shape.  _shapename!_ is the name of the shape from which you want to retrieve the text.  <br/> |
| _maximumwidth_ <br/> |Optional  <br/> |**Numeric** <br/> |The maximum width of the text block.  <br/> |
   
### Return value

String
  
## Remarks

The TEXTWIDTH function is commonly used to adjust the width of a shape to fit the text it contains.
  
If  _sheetN!_ is omitted, the default shape is the current shape. 
  
If  _maximumwidth_ is specified, the result is the longest line of text that fits within  _maximumwidth_. If  _maximumwidth_ is omitted, the result is the total width of the text. 
  
## Example

TEXTWIDTH(TheText) 
  
Returns the total length of the text in the current shape. 
  

