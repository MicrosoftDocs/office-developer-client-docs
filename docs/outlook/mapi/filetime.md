---
title: "FILETIME"
description: Describes FILETIME and provides syntax, members, and additional remarks.
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FILETIME
api_type:
- COM
ms.assetid: 4af8e79a-697e-44a1-8576-fdc57726e9ef
---

# FILETIME

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Holds an unsigned 64-bit date and time value for a file. This value represents the number of 100-nanosecond units since the start of January 1, 1601. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _FILETIME
{
  DWORD dwLowDateTime;
  DWORD dwHighDateTime;
} FILETIME, FAR *LPFILETIME;

```

## Members

 **dwLowDateTime**
  
> Low-order 32 bits of the file time value. 
    
 **dwHighDateTime**
  
> High-order 32 bits of the file time value.
    
## Remarks

A property of type PT_SYSTIME has a **FILETIME** structure for its value. Such a property has a **FILETIME** data type for the **Value** member in its definition in an [SPropValue](spropvalue.md) structure. 
  
The definition of the **FILETIME** structure is in the _Win32 Programmer's Reference_ and in the MAPI header file Mapidefs.h. MAPI defines the structure conditionally to make sure that it is defined when the Win32 definition is unavailable. 
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

