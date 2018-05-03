---
title: "TZDEFINITION"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 0ae21571-2299-6407-807c-428668bb6798
description: "Represents an entire time zone including all historical, current, and future time zone shift rules for daylight saving time."
---

# TZDEFINITION

Represents an entire time zone including all historical, current, and future time zone shift rules for daylight saving time.
  
## Quick Info

```
typedef struct { 
    WORD     wFlags;  
    LPWSTR   pwszKeyName; 
    WORD     cRules; 
    TZRULE*  rgRules; 
} TZDEFINITION;
```

## Members

 _wFlags_
  
> Indicates that the key name that represents the time zone in the Windows registry is valid. Because each time zone should always be identified by a key name, this member should always have the value **TZDEFINITION_FLAG_VALID_KEYNAME**.
    
 _pwszKeyName_
  
> The name of the key for this time zone in the Windows registry. This name must not be localized. It has a maximum size of **MAX_PATH**, which is defined in the Windows Software Development Kit (SDK) header file windows.h. 
    
 _cRules_
  
> The number of time zone rules for this definition. The maximum number of rules is **TZ_MAX_RULES**. 
    
 _rgRules_
  
> An array of rules that describe when shifts occur.
    
## Remarks

There must be at least one rule in  *rgRules*  . The first rule in  *rgRules*  is considered to be the rule to use until the second rule starts, regardless of the  *stStart*  on the first rule. 
  
The rules should be sorted from oldest to newest. There is no overlap allowed between rules, so a prior rule is deemed to end when a new rule starts.
  
## See also

#### Concepts

[Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)
  
[About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)
  
[HrCreateApptRebaser](hrcreateapptrebaser.md)

