---
title: "FORMATEX Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251590
 
ms.localizationpriority: medium
ms.assetid: d375c971-fee2-baa3-dc4f-a26018e70e8a
description: "Returns the result of expression evaluated in srcUnit as a string formatted according to format expressed in dstUnit."
---

# FORMATEX Function

Returns the result of expression evaluated in srcUnit as a string formatted according to format expressed in dstUnit.
  
## Syntax

FORMATEX(** *expression* **," ** *format* ** ",[ ** *srcUnit* ** ],[ ** *dstUnit* ** ],[ ** *langID* ** ][, ** *calID* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _expression_ <br/> |Required  <br/> |**String** <br/> |A combination of constants, operators, functions, and references to ShapeSheet cells that results in a value.  <br/> |
| _format_ <br/> |Required  <br/> |**String** <br/> |The format picture used to format the string. For more information about format pictures, see [About Format Pictures](about-format-pictures.md).  <br/> |
| _srcUnit_ <br/> |Optional  <br/> |**String** <br/> | Units used to evaluate expression (in, cm, and so forth).  <br/> |
| _dstUnit_ <br/> |Optional  <br/> |**String** <br/> |Units to use for the result of expression (in, cm, and so forth).  <br/> |
| _langID_ <br/> |Optional  <br/> |**Number** <br/> |The language used when formatting Microsoft Office System date/time pictures.  <br/> |
| _calID_ <br/> |Optional  <br/> |**Number** <br/> |The calendar used when formatting Microsoft Office System date/time pictures.  <br/> |
   
### Return value

String
  
## Remarks

The type of the expression and the type specified in the format picture govern the behavior of the returned string. The format must be appropriate for the type of expression.
  
The srcUnit argument is used to scale untyped expression results, such as 3 + 4. If the result of expression has an explicit type, such as 3 ft + 8 ft, then srcUnit is ignored.
  
The dstUnit argument is used to specify the units used for the formatted result. If dstUnit is not specified, the units for the result of the expression are used.
  
Returns an error if the result of expression and the type expected in format are of a different kind, if there are syntax errors in format, or if it does not recognize the units passed as srcUnit or dstUnit.
  
## Example

FORMATEX(5.5, "0.00 u", "cm", "ft") 
  
Returns 0.18 feet. 
  

