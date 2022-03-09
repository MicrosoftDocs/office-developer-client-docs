---
title: "MSOSHADE Function" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 905cd1cc-14d3-5d37-89c4-f8461a03dda2
description: "Modifies the color by decreasing its luminosity by the specified percentage."
---

# MSOSHADE Function

Modifies the color by decreasing its luminosity by the specified percentage.
  
## Version Information

Version Added: Visio 2010
  
## Syntax

MSOSHADE(***color***, ***-deltaLum*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *color* <br/> |Required  <br/> |**RGB** <br/> |The standard RGB (red, green, blue) color value or reference to a color. |
| *-deltaLum* <br/> |Required  <br/> |**Integer** <br/> |The percentage change toward white (-100%) or black (100%) from the *color* value. |

## Remarks

The closer the *color* value is to white or black, the smaller the change to the shade that is produced by a specific *-deltaLum* value.
  