---
title: "SzFindCh"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SzFindCh
api_type:
- COM
ms.assetid: 3406d060-bfea-4cea-8253-2a9aeb9e8147
description: "Searches for the first occurrence of a character in a null-terminated string. Searches in the Unicode and DBCS formats are supported."
---

# SzFindCh
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Searches for the first occurrence of a character in a null-terminated string. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LPSTR SzFindCh(
  LPCSTR lpsz,
  USHORT ch
);
```

## Parameters

_lpsz_
  
> [in] Pointer to the null-terminated string to be searched. 
    
_ch_
  
> [in] The character to be searched for.
    
## Return value

**SzFindCh** returns a pointer to the first occurrence of the character in the string. If the character does not occur anywhere in the string, or if the _lpsz_ parameter is NULL, a value of NULL is returned. 
  
## Remarks

The **SzFindCh** function searches for an exact match only; it is sensitive to case and diacritical differences. Searches in the Unicode and DBCS formats are supported. 
  

