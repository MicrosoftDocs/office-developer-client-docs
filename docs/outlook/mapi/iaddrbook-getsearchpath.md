---
title: "IAddrBookGetSearchPath"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.GetSearchPath
api_type:
- COM
ms.assetid: 43b51a66-71fa-4e10-93e4-d533b48af4de
description: "Last modified: July 23, 2011"
---

# IAddrBook::GetSearchPath

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns an ordered list of entry identifiers of the containers to be included in the name resolution process initiated by the [IAddrBook::ResolveName](iaddrbook-resolvename.md) method. 
  
```cpp
HRESULT GetSearchPath(
  ULONG ulFlags,
  LPSRowSet FAR * lppSearchPath
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the strings returned in the search path. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lppSearchPath_
  
> [out] A pointer to a pointer to an ordered list of container entry identifiers. **GetSearchPath** stores the ordered list in an [SRowSet](srowset.md) structure. If there are no containers in the address book hierarchy, zero is returned in the **SRowSet** structure. 
    
## Return value

S_OK 
  
> The search path was successfully retrieved.
    
## Remarks

Clients and service providers call the **GetSearchPath** method to get the search path that is used to resolve names with the **ResolveName** method. Typically, clients call the [IAddrBook::SetSearchPath](iaddrbook-setsearchpath.md) method to establish a container search path in the profile before they call **GetSearchPath** to retrieve it. However, calling **SetSearchPath** is optional. 
  
If **SetSearchPath** has never been called, **GetSearchPath** builds a path by working through the address book's hierarchy tables. The default search path established by **GetSearchPath** consists of the following containers in the following order: 
  
1. The first container with read/write permission, usually the personal address book (PAB).
    
2. Every container that has its **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) property set to DT_GLOBAL. This setting indicates that the container holds recipients. 
    
3. The container designated as the default, if there are no containers that have the DT_GLOBAL flag set in their **PR_DISPLAY_TYPE** property and the default container differs from the first container with read/write permission. 
    
If **SetSearchPath** has been called, **GetSearchPath** builds a path by using the address book containers that have been stored in the profile. **GetSearchPath** validates this path before it returns it to the caller. 
  
After the first call to **SetSearchPath**, subsequent calls to **SetSearchPath** must be used to modify the search path returned by **GetSearchPath**. In other words, the calling client or provider does not receive the default search path after the first call to **SetSearchPath**.
  
## See also



[IAddrBook::SetSearchPath](iaddrbook-setsearchpath.md)
  
[SRowSet](srowset.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

