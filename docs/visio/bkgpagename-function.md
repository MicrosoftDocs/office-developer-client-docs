---
title: "BKGPAGENAME Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82253219
 
ms.localizationpriority: medium
ms.assetid: f6e410ef-54d5-9c08-926b-97a2a9786622
description: "Returns a background page name as a string."
---

# BKGPAGENAME Function

Returns a background page name as a string.
  
## Syntax

BKGPAGENAME (***langID_opt*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *langID_opt* <br/> |Optional  <br/> |**Numeric** <br/> |Use to specify a language for the string the function returns. Use 0 (default value) to specify the local language. Use 750 to specify universal language. |

### Return value

String
  
## Remarks

If the page for which you are using the function doesn't have a background page, the string "\<no background\>" is returned.
  
If you pass an illegal language code, the local language is used.
  