---
title: "MNLS_lstrcmpW"
description: "Describes the syntax, parameters, return value, and remarks for MNLS_lstrcmpW, which compares two Unicode strings."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: d26c59d7-c839-426f-8693-727fc6bef67e
---

# MNLS_lstrcmpW

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two Unicode strings.
  
```cpp
int MNLS_lstrcmpW(
  LPCWSTR lpString1,
  LPCWSTR lpString2);
```

## Parameters

 _lpString1_
  
> [in] Pointer to the first Unicode string to compare.
    
 _lpString2_
  
> [in] Pointer to the second Unicode string to compare.
    
## Return value

Returns the values described for an equivalent call to **MNLS_CompareStringW** except for CSTR_EQUAL. 
  
## Remarks

 _MNLS_lstrcmpW_ performs a comparison by calling [MNLS_CompareStringW](mnls_comparestringw.md) with a locale of GetUserDefaultLCID, 0 for flags, and -1 for cch1 and cch2. 
  
## See also



[GetUserDefaultLCID](https://msdn.microsoft.com/library/dd318135%28VS.85%29.aspx)

