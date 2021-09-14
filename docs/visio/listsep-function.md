---
title: "LISTSEP Function"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251882
 
ms.localizationpriority: medium
ms.assetid: 73dc5981-2c8c-e76e-e4bd-e65a7c8db242
description: "Returns the list-separator string for the current user locale."
---

# LISTSEP Function

Returns the list-separator string for the current user locale.
  
## Syntax

LISTSEP ()
  
### Return value

String
  
## Example

SETF(GETREF(user.extent), "MAX(Width" &amp; ListSep() &amp; "Height)") 
  

