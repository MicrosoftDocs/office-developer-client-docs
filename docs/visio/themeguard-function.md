---
title: "THEMEGUARD Function"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a556eadc-9ee6-7a29-ca05-6250b612790c
description: "Guards the formatting cells of a shape to ensure that they use appropriate aspects of the current theme."
---

# THEMEGUARD Function

Guards the formatting cells of a shape to ensure that they use appropriate aspects of the current theme.
  
## Syntax

THEMEGUARD()
  
## Remarks

Applying the THEMEGUARD function to a cell does not guard against manual formatting in the same way that applying the GUARD function does. If you apply formatting to the shape in the user interface or programmatically, by means of Automation, the THEMEGUARD formula is overridden, unless you include the SETATREFEXPR function in the formula to store the manual formatting value. 
  
## Example

```
Shape.FillForegnd = THEMEGUARD(THEME("AccentColor2")
```

Specifies that the shape take the Accent 2 color from the current theme, rather than the main theme fill color.
  

