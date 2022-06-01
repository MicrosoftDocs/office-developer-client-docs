---
title: "MNLS_lstrcpyW"
description: "Describes the syntax, parameters, return value, and remarks for NLS_lstrcpyW, which copies a string to a buffer."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: a0f92c2d-b5ba-4558-b8a2-484b2db32bec
---

# MNLS_lstrcpyW

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies a string to a buffer.
  
> [!CAUTION]
> Do not use. Consider using [StringCchCopy](https://msdn.microsoft.com/library/ms647527%28VS.85%29.aspx) instead. 
  
```cpp
LPWSTR MNLS_lstrcpyW(
 LPWSTR lpString1,
LPCWSTR lpString2);
```

## Parameters

lpString1
  
> [out] A buffer to receive the contents of the string pointed to by the lpString2 parameter.
    
lpString2
  
> [in] The null-terminated string to be copied.
    
## Return value

If the function succeeds, the return value is a pointer to the buffer.
  
If the function fails, the return value is NULL and lpString1 may not be null-terminated.
  
## Remarks

This function wraps the **lstrcpy** function. For more information, see [lstrcpy](https://msdn.microsoft.com/library/ms647490%28VS.85%29.aspx).
  
## See also



[lstrcpy](https://msdn.microsoft.com/library/ms647490%28VS.85%29.aspx)

