---
title: "FGetComponentPath"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.FGetComponentPath
api_type:
- COM
ms.assetid: 2a303458-3283-409a-bc3b-b891f3fcfc22
---

# FGetComponentPath

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the path to the private Mapi32.dll.
  
```cpp
BOOL FGetComponentPath(
  LPCSTR szComponent,
  LPSTR szQualifier,
  LPSTR szDllPath,
  DWORD cchBufferSize,
  BOOL fInstall
);
```

## Parameters

 _szComponent_
  
> [in] The MSIComponentID reg key described in [Mapi32.dll Stub Registry Settings](https://msdn.microsoft.com/library/dd162409.aspx).
    
 _szQualifier_
  
> [in] The MSIApplicationLCID or MSIOfficeLCID subkey described in [Choose a Specific Version of MAPI to Load](how-to-choose-a-specific-version-of-mapi-to-load.md). Callers can pass **null** if there is no qualifier. 
    
 _szDllPath_
  
> [in] The path to the private Mapi32.dll, which has full MAPI functionality (the same exports as the Mapi32.dll).
    
 _cchBufferSize_
  
> [in] The size of  _szDllPath_, in characters.
    
 _fInstall_
  
> [in] Tells MAPI to install the private Mapi32.dll component if it is absent.
    
## Return value

 **true**
  
> The path was found.
    
 **false**
  
> The path was not found.
    
## Remarks

Use the **FGetComponentPath** function when you need to get the path to the private Mapi32.dll. 
  
## See also



[Choose a Specific Version of MAPI to Load](how-to-choose-a-specific-version-of-mapi-to-load.md)


[Mapi32.dll Stub Registry Settings](https://msdn.microsoft.com/library/dd162409.aspx)

