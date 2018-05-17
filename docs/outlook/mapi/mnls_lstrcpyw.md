---
title: "MNLS_lstrcpyW"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a0f92c2d-b5ba-4558-b8a2-484b2db32bec
description: "Last modified: June 18, 2012"
---

# MNLS_lstrcpyW

 
  
**Applies to**: Outlook 
  
Copies a string to a buffer.
  
> [!CAUTION]
> Do not use. Consider using [StringCchCopy](http://msdn.microsoft.com/en-us/library/ms647527%28VS.85%29.aspx) instead. 
  
```
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

This function wraps the **lstrcpy** function. For more information, see [lstrcpy](http://msdn.microsoft.com/en-us/library/ms647490%28VS.85%29.aspx).
  
## See also

#### Other resources

[lstrcpy](http://msdn.microsoft.com/en-us/library/ms647490%28VS.85%29.aspx)

