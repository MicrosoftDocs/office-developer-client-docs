---
title: "DECIMALSEP Function"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251883
 
ms.localizationpriority: medium
ms.assetid: 091fe401-05b2-464f-9333-7bb7118cd7cd
description: "Returns the decimal separator string for the current user locale."
---

# DECIMALSEP Function

Returns the decimal separator string for the current user locale.
  
## Syntax

DECIMALSEP( )
  
## Example

SETF(GETREF(user.size), user.wholePart &amp; DECIMALSEP() &amp; user.fracPart) 
  

