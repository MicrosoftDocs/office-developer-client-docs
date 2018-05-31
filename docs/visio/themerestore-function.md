---
title: "THEMERESTORE Function"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: ca7e6621-f39b-64dd-3594-41d74da21a94
description: "Stores the local formatting value of a shape when you apply a theme so that you can restore the local formatting if the user subsequently removes the theme."
---

# THEMERESTORE Function

Stores the local formatting value of a shape when you apply a theme so that you can restore the local formatting if the user subsequently removes the theme.
  
## Syntax

THEMERESTORE()
  
## Example

```vb
Shape.FillForegnd = THEME("FillColor") + THEMERESTORE(RGB(255,102,0)
```

Restores local fill color formatting previously applied to a shape when the current theme is removed.
  

