---
title: "SzFindLastCh"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SzFindLastCh
api_type:
- COM
ms.assetid: 7c3e5a71-7b78-4328-b8ee-265cc4da4be5
description: "Searches for the last occurrence of a character in a null-terminated string."
---

# SzFindLastCh

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Searches for the last occurrence of a character in a null-terminated string. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LPSTR SzFindLastCh(
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

 **SzFindLastCh** returns a pointer to the last occurrence of the character in the string. If the character does not occur anywhere in the string, or if the _lpsz_ parameter is NULL, a value of NULL is returned. 
  
## Remarks

The **SzFindLastCh** function searches for an exact match only; it is sensitive to case and diacritical differences. Searches in the Unicode and DBCS formats are supported. 
  

