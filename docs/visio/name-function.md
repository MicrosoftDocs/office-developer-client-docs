---
title: "NAME Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251580
 
ms.localizationpriority: medium
ms.assetid: 1ca67a09-9df2-37f5-b269-e761d76bb011
description: "Returns a sheet's name as a string."
---

# NAME Function

Returns a sheet's name as a string.
  
## Syntax

NAME (** *langID_opt* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _langID_opt_ <br/> |Optional  <br/> |**Number** <br/> |Use to specify a language for the string the function returns. Use 0 (default value) to specify the local language. Use 750 to specify universal language. |
   
### Return value

String
  
## Remarks

If you pass an illegal language code, the local language is used. 
  

