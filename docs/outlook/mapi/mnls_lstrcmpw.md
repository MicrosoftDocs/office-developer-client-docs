---
title: "MNLS_lstrcmpW"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d26c59d7-c839-426f-8693-727fc6bef67e
description: "Last modified: June 18, 2012"
---

# MNLS_lstrcmpW

 **Last modified:** June 18, 2012 
  
 * **Applies to:** Outlook * 
  
Compares two Unicode strings.
  
```
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

#### Other resources

[GetUserDefaultLCID](http://msdn.microsoft.com/en-us/library/dd318135%28VS.85%29.aspx)

