---
title: "PAGENAME Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251577
 
ms.localizationpriority: medium
ms.assetid: 12e45f46-e773-9445-4c7f-c726ab648671
description: "Returns the page name as a string."
---

# PAGENAME Function

Returns the page name as a string.
  
## Syntax

PAGENAME (** *langID_opt* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _langID_opt_ <br/> |Optional  <br/> |**Number** <br/> |Use to specify a language for the string the function returns. Use 0 (default value) to specify the local language. Use 750 to specify universal language.  <br/> |
   
### Return value

String
  
## Remarks

If you pass an illegal language code, the local language is used.
  

