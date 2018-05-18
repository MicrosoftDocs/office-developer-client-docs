---
title: "FBStatus"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: f2d6a11e-847d-6bbe-cd77-e78ee961cb12
description: "An enumeration for the free/busy status of free/busy blocks."
---

# FBStatus

An enumeration for the free/busy status of free/busy blocks.
  
## Quick info

```
enum  
    { 
      fbFree      = 0, 
      fbTentative = fbFree + 1, 
      fbBusy      = fbTentative + 1, 
      fbOutOfOffice = fbBusy + 1 
    }

```

## Remarks

The free/busy status of a block of time determines how it is displayed on a calendar: **Free**, **Busy**, **Tentative**, or **Out of Office**. 
  
## See also



[FBBlock_1](fbblock_1.md)
  
[IEnumFBBlock::Next](ienumfbblock-next.md)

