---
title: "MNLS_lstrlenW"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d342a956-1164-4c9c-b0bb-7a0b72dc97fc
description: "Last modified: February 21, 2012"
---

# MNLS_lstrlenW

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines the length of the specified Unicode string, excluding the terminating null character.
  
> [!TIP]
> Consider using [StringCchLength](http://msdn.microsoft.com/en-us/library/ms647539%28VS.85%29.aspx) instead. 
  
```cpp
int MNLS_lstrlen(
  LPCWSTR lpsz);
```

## Parameters

 _lpsz_
  
> [in] The null-terminated Unicode string to be checked.
    
## Return value

The function returns an integer with the length of the string. It is a count of characters in the string, excluding the terminating null character. If  _lpsz_ is NULL, the function returns zero. 
  
## Remarks

This function wraps the **lstrlen** function. For more information, see [lstrlen](http://msdn.microsoft.com/en-us/library/ms647492%28VS.85%29.aspx).
  
## See also



[lstrlen](http://msdn.microsoft.com/en-us/library/ms647492%28VS.85%29.aspx)
  
[StringCchLength](http://msdn.microsoft.com/en-us/library/ms647539%28VS.85%29.aspx)

