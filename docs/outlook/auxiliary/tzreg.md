---
title: "TZREG"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: a353e1a3-0187-20af-b9ba-43438f6024d5
description: "Defines when daylight saving time starts, when the return to standard time occurs, and how many hours the daylight saving shift is."
---

# TZREG

Defines when daylight saving time starts, when the return to standard time occurs, and how many hours the daylight saving shift is.
  
## Quick info

```cpp
typedef struct RenTimeZone { 
    long        lBias;  
    long        lStandardBias; 
    long        lDaylightBias; 
    SYSTEMTIME  stStandardDate; 
    SYSTEMTIME  stDaylightDate; 
} TZREG; 

```

## Members

_lBias_
  
> The offset from Greenwich Mean Time (GMT).
    
_lStandardBias_
  
> The offset from bias during standard time.
    
_lDaylightBias_
  
> The offset from bias during daylight saving time.
    
_stStandardDate_
  
> The time to switch to standard time.
    
_stDaylightDate_
  
> The time to switch to daylight saving time.
    
## Remarks

This structure is similar to **TIME_ZONE_INFORMATION**. This is the structure used by legacy clients to store time zone information for recurring meetings.
  
## See also

- [About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)  
- [HrCreateApptRebaser](hrcreateapptrebaser.md)  
- [TZRULE](tzrule.md)

