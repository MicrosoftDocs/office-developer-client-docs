---
title: "ScLocalPathFromUNC"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScLocalPathFromUNC
api_type:
- COM
ms.assetid: ef5eb5c6-251e-4a3a-8855-7c28804a29ab
description: "Last modified: March 09, 2015"
---

# ScLocalPathFromUNC

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Locates a local path counterpart to the given universal naming convention (UNC) path. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScLocalPathFromUNC(
  LPSTR szUNC,
  LPSTR szLocal,
  UINT cchLocal
);
```

## Parameters

 _szUNC_
  
> [in] A path in the format \\[ _server_]\[ _share_]\[ _path_] of a file or directory.
    
 _szLocal_
  
> [out] A path in the format [ _drive:_]\[ _path_] of the same file or directory as for the  _szUNC_ parameter. 
    
 _cchLocal_
  
> [in] Size of the buffer for the output string.
    
## Return value

S_OK
  
> A local path was successfully located.
    
MAPI_E_TOO_BIG
  
>  _szLocal_ was not large enough to hold the result. 
    
S_FALSE
  
> The UNC string was already a local path.
    
MAPI_E_NOT_FOUND
  
> A local path was not found.
    
## See also



[ScUNCFromLocalPath](scuncfromlocalpath.md)

