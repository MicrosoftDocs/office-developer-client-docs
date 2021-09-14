---
title: "IsBadBoundedStringPtr"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 888c60e3-7376-4d66-8ee2-ce81abafb185
description: "Last modified: March 09, 2015"
---

# IsBadBoundedStringPtr

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Verifies that the calling process has read access to the specified range of memory.
  
|||
|:-----|:-----|
|Header file:  <br/> |mapiwin.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers.  <br/> |
   
```cpp
BOOL IsBadBoundedStringPtr(
  const void FAR* lpsz,
  UINT cchMax
);
```

## Parameters

 _lpsz_
  
> [in] Pointer to a null-terminated ASCII string.
    
 _cchMax_
  
> [in] The maximum size of the string, in CHARs. The function checks for read access in all characters up to the terminating null character of the string, or up to the number of characters specified by this parameter, whichever is smaller. If this parameter is zero, the return value is zero.
    
## Return value

The return value is zero when the calling process has read access to all characters up to the terminating null character of the string, or read access up to the number of characters specified by  _cchMax_.
  
The return value is non-zero when the calling process does not have read access to all characters up to the terminating null character of the string, or read access up to the number of characters specified by  _cchMax_.
  
## Remarks

The **IsBadBoundedStringPtr** function is equivalent to using **IsBadStringPtr**.
  
## See also



[IsBadStringPtr](https://msdn.microsoft.com/library/windows/desktop/aa366714%28v=vs.85%29.aspx)

