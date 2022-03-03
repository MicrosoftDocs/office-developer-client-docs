---
title: "IAddrBookSetSearchPath"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.SetSearchPath
api_type:
- COM
ms.assetid: fbff82de-77d3-411e-a30c-a37cefdd92fc
---

# IAddrBook::SetSearchPath

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets a new search path in the profile that is used for the name resolution process. 
  
```cpp
HRESULT SetSearchPath(
  ULONG ulFlags,
  LPSRowSet lpSearchPath
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpSearchPath_
  
> [in] A pointer to the [SRowSet](srowset.md) structure used to hold the search path. The first property for each **aRow** member in **SRowSet** must be **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)).
    
## Return value

S_OK 
  
> The search path was successfully set.
    
MAPI_E_MISSING_REQUIRED_COLUMN 
  
> One of the containers described in the **SRowSet** structure did not include its **PR_ENTRYID** property. 
    
## Remarks

Clients and service providers call the **SetSearchPath** method to save changes that were made to the container search order that is used to resolve names with the [IAddrBook::ResolveName](iaddrbook-resolvename.md) method. The search path is saved between instances of a session. 
  
Clients and providers do not have to call the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to make the search path changes permanent. 
  
## See also



[IAddrBook::GetDefaultDir](iaddrbook-getdefaultdir.md)
  
[IAddrBook::GetPAB](iaddrbook-getpab.md)
  
[IAddrBook::GetSearchPath](iaddrbook-getsearchpath.md)
  
[PidTagContainerFlags Canonical Property](pidtagcontainerflags-canonical-property.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

