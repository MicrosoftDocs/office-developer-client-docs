---
title: "MID Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027310
 
localization_priority: Normal
ms.assetid: 5041d957-1bd9-4d76-cf43-7b4fcd1e7dec
description: "Returns a specific number of characters from a text string, starting at the position you specify, based on the number of characters you specify."
---

# MID Function (VisioShapeSheet)

Returns a specific number of characters from a text string, starting at the position you specify, based on the number of characters you specify.
  
## Syntax

MID (** *text* **, ** *start_num* **, ** *num_chars* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _text_ <br/> |Required  <br/> |**String** <br/> |The text string that contains the characters you want to extract.  <br/> |
| _start_num_ <br/> |Required  <br/> |**Number** <br/> |The position of the first character you want to extract. The first character in the text string is position 1.  <br/> |
| _num_chars_ <br/> |Required  <br/> |**Number** <br/> |The number of characters to return.  <br/> |
   
### Return value

String
  
## Remarks

If  *start_num*  is: 
  
- Greater than the length of  *text*  , MID returns "" (empty text). 
    
- Less than the length of  *text*  , but  *start_num*  plus  *num_chars*  exceeds the length of  *text*  , MID returns the characters up to the end of  *text*  . 
    
- Less than 1, MID returns the #VALUE! error value. 
    
If  *num_chars*  is negative, MID returns the #VALUE! error value. 
  
## Example

MID ("SSN 999-99-9999",5,11) 
  
Returns 999-99-9999. 
  

