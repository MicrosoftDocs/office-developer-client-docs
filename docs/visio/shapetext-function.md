---
title: "SHAPETEXT Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251788
 
localization_priority: Normal
ms.assetid: 87ea5e8f-c3e0-009f-4bf8-8c34fbdb83a6
description: "Gets the text from a shape."
---

# SHAPETEXT Function

Gets the text from a shape. 
  
## Syntax

SHAPETEXT ( ** *shapename!TheText* ** ** *[,flag]* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _shapename!TheText_ <br/> |Required  <br/> ||A reference to the cell named TheText in the target shape.  _Shapename!_ is the name of the shape from which you want to retrieve the text.  <br/> |
| _flag_ <br/> |Optional  <br/> |**Numeric** <br/> |A bit that specifies the format of the text. The default flag (0) shows the text exactly as it is shown in the shape.  <br/> |
   
### Return value

String
  
## Remarks

You can use any combination of the following flags with the SHAPETEXT function.
  
|**Flag**|**Description**|
|:-----|:-----|
|0  <br/> |Show text exactly as shown in shape.  <br/> |
|1  <br/> |Include discretionary hyphens.  <br/> |
|2  <br/> |Don't include expanded text in fields.  <br/> |
|4  <br/> |Convert tabs to a single space.  <br/> |
|8  <br/> |Convert tabs to a set of spaces.  <br/> |
|16  <br/> |Convert carriage returns and line feeds to spaces.  <br/> |
|32  <br/> |Convert typographer quotes to regular quotes.  <br/> |
|64  <br/> |Convert adjacent white space to a single space.  <br/> |
   
## Example 1

SHAPETEXT(sheetN!theText)
  
Returns the text of the shape named sheetN, exactly as it is shown in the shape.
  
## Example 2

SHAPETEXT(theText)
  
Returns the text of the current shape exactly as it is shown in the shape.
  
## Example 3

SHAPETEXT(theText, 84)
  
Returns the text of the current shape. It also converts adjacent white space to a single space (64), converts carriage returns and line feeds to spaces (16), and converts tabs to a single space (4). The sum of these flags is 84.
  

