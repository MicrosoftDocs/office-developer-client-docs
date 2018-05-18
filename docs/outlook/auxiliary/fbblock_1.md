---
title: "FBBlock_1"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: da67171d-d25f-3424-1409-33189ac63a12
description: "Defines a free/busy block of data. This is an item on a calendar represented by an appointment or meeting request."
---

# FBBlock_1

Defines a free/busy block of data. This is an item on a calendar represented by an appointment or meeting request.
  
## Quick info

```
typedef struct  tagFBBlock_1 
    { 
    long m_tmStart; 
    long m_tmEnd; 
    FBStatus m_fbstatus; 
    }FBBlock_1; 

```

## Members

 _m_tmStart_
  
> The start time for the block, expressed in relative time. For more information, see [Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md).
    
 _m_tmEnd_
  
> The end time for the block, expressed in relative time.
    
 _m_fbStatus_
  
> The free/busy status for this block, indicating whether the user is out-of-office, busy, tentative, or free, during the time period between  _m_tmStart_ and  _m_tmEnd_.
    
## See also



[FBStatus](fbstatus.md)
  
[IEnumFBBlock::Next](ienumfbblock-next.md)
  
[Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md)

