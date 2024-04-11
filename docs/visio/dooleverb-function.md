---
title: "DOOLEVERB Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251421
 
ms.localizationpriority: medium
ms.assetid: d276c122-6326-75a7-220c-6a78e94e0db0
description: "Executes a verb for the OLE object."
---

# DOOLEVERB Function

Executes a verb for the OLE object.
  
## Syntax

DOOLEVERB(" ***verb*** ")
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *"verb"* <br/> |Required  <br/> |**String** <br/> |The verb to execute. |

## Remarks

In earlier versions of Visio, this function appears as _DOOLEVERB. Visio versions 4.0 and later accept either style.
  
## Example

DOOLEVERB("edit")
  
Runs the OLE object program and displays the linked or embedded object so that it can be edited.
  