---
title: "TZRULE"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 75ed353c-7d3e-e148-4057-715e82a0f32c
description: "Specifies information for a time zone rule about when daylight saving time starts, and the year in which that time zone rule first takes effect."
---

# TZRULE

Specifies information for a time zone rule about when daylight saving time starts, and the year in which that time zone rule first takes effect. 
  
## Quick info

```cpp
typedef struct { 
    WORD        wFlags;  
    SYSTEMTIME  stStart; 
    TZREG       TZReg; 
} TZRULE;
```

## Members

_wFlags_
  
> The flags set for this member identify specific details for this time zone rule. The possible flags are as follows:
    
   - **TZRULE_FLAG_EFFECTIVE_TZREG** —Identifies the rule as the one that should be used currently. Only one rule can be marked as the effective rule. All other rules are for comparison purposes only. 
    
   - **TZRULE_FLAG_RECUR_CURRENT_TZREG** —On recurring meetings, identifies the rule as matching the rule in [PidLidTimeZoneStruct](https://msdn.microsoft.com/library/2acf0036-2f3e-4f90-8614-7aa667860f74%28Office.15%29.aspx). This can be used to detect whether **PidLidTimeZoneStruct** has been modified significantly by a legacy client, which would be otherwise unaware of the new, more complete property. 
    
_stStart_
  
> The time in Coordinated Universal Time (UTC) that the time zone rule started.
    
_TZReg_
  
> The time zone information for the time zone rule.
    
## Remarks

This structure augments [TZREG](tzreg.md) by providing additional information indicating when time zone rules take effect. 
  
## See also

- [About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md) 
- [Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)
- [HrCreateApptRebaser](hrcreateapptrebaser.md)
- [TZDEFINITION](tzdefinition.md)

