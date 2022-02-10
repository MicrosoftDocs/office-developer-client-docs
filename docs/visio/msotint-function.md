---
title: "MSOTINT Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 1bae0af9-229d-e114-4feb-bf6d7a7d8b08
description: "Modifies the color by increasing its luminosity by the specified percentage."
---

# MSOTINT Function

Modifies the color by increasing its luminosity by the specified percentage.
  
## Version Information

Version Added: Visio 2010 
  
## Syntax

MSOTINT(** *color* **, ** *deltaLum* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _color_ <br/> |Required  <br/> |**RGB** <br/> |The standard RGB (red, green, blue) color value or reference to a color. |
| _deltaLum_ <br/> |Required  <br/> |**Integer** <br/> |The percentage change toward white (-100%) or black (100%) from the  _color_ value. |
   
## Remarks

The closer the  _color_ value is to white or black, the smaller the change to the tint that is produced by a specific  _deltaLum_ value. 
  

