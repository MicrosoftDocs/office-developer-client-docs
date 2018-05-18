---
title: "MASTERNAME Function"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251581
localization_priority: Normal
ms.assetid: 519d79d4-9178-2231-c26d-aa7f31a43412
description: "Returns a sheet's master name as a string, or returns the string 'no master' if the sheet doesn't have a master."
---

# MASTERNAME Function

Returns a sheet's master name as a string, or returns the string "\<no master\>" if the sheet doesn't have a master.
  
## Syntax

MASTERNAME ([ ** *langID_opt* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _langID_opt_ <br/> |Optional  <br/> |**Number** <br/> |Use to specify a language for the string the function returns. Use 0 (default value) to specify the local language. Use 750 to specify universal language.  <br/> |
   
### Return value

String
  
## Remarks

If you pass an illegal language code, the local language is used. 
  

