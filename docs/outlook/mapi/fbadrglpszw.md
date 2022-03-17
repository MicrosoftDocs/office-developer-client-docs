---
title: "FBadRglpszW"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FBadRglpszW
api_type:
- COM
ms.assetid: 880eb35d-7045-4fdd-bb33-0f14557a7316
description: "Validates all strings in an array of Unicode strings."
---

# FBadRglpszW

**Applies to**: Outlook 2013 | Outlook 2016
  
Validates all strings in an array of Unicode strings.
  
|**Info**|**Value**|
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |

```cpp
BOOL FBadRglpszW(
  LPWSTR FAR * lppszW,
  ULONG cStrings
);
```

## Parameters

 _lppszW_
  
> [in] Pointer to an array of null-terminated Unicode strings.

 _cStrings_
  
> [in] Count of strings in the array pointed to by the _lppszW_ parameter.

## Return value

TRUE
  
> One or more of the strings in the specified array are invalid.

FALSE
  
> The strings in the specified array are valid.
