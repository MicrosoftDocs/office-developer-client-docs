---
title: "FILETIME"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FILETIME
api_type:
- COM
ms.assetid: 4af8e79a-697e-44a1-8576-fdc57726e9ef
description: "Last modified: March 09, 2015"
---

# FILETIME

  
  
**Applies to**: Outlook 
  
Holds an unsigned 64-bit date and time value for a file. This value represents the number of 100-nanosecond units since the start of January 1, 1601. 
  
|||
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
  
The definition of the **FILETIME** structure is in the  _Win32 Programmer's Reference_ and in the MAPI header file Mapidefs.h. MAPI defines the structure conditionally to make sure that it is defined when the Win32 definition is unavailable. 
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

