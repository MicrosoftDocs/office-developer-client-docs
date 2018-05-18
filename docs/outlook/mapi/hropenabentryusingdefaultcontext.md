---
title: "HrOpenABEntryUsingDefaultContext"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 17cba69b-2b25-4b99-99d9-ec68fb8a35b5
description: "Last modified: March 09, 2015"
---

# HrOpenABEntryUsingDefaultContext

  
  
**Applies to**: Outlook 
  
Performs the same function as [HrOpenABEntryWithExchangeContext](hropenabentrywithexchangecontext.md) except that it uses the legacy **emsmdbUID** as the  _pEmsmdbUID_ parameter. Do not use this function unless you cannot obtain the correct **emsmdbUID** for the call to [HrOpenABEntryWithExchangeContext](hropenabentrywithexchangecontext.md).
  
|||
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrOpenABEntryUsingDefaultContext(
  LPMAPISESSION pmsess,
  LPADRBOOK pAddrBook,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _pmsess_
  
> [in] The logged on **IMAPISession**. It cannot be NULL.
    
 _pAddrBook_
  
> [in] The address book used to open the entry identifier. It cannot be NULL.
    
 _cbEntryID_
  
> [in] The byte count of the entry identifier specified by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
>  [in] A pointer to the entry identifier that represents the address book entry to open. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) of the interface that is used to access the open entry. Passing NULL returns the standard interface of the object. For messaging users, the standard interface is [IMailUser : IMAPIProp](imailuserimapiprop.md). For distribution lists it is [IDistList : IMAPIContainer](idistlistimapicontainer.md), and for containers it is [IABContainer : IMAPIContainer](iabcontainerimapicontainer.md). Callers can set  _lpInterface_ to the appropriate standard interface or an interface in the inheritance hierarchy. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the entry is opened. The following flags can be set:
    
MAPI_BEST_ACCESS
  
> Requests that the entry be opened with the maximum allowed network and client permissions. For example, if the client has read and write permission, the address book provider attempts to open the entry with read and write permission. The client can retrieve the access level that was granted by calling the [IMAPIProp::GetProps](imapiprop-getprops.md) method of the open entry and retrieving the PR_ACCESS_LEVEL (PidTagAccessLevel) property. 
    
MAPI_CACHE_ONLY
  
> Uses only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange address book provider.
    
MAPI_DEFERRED_ERRORS
  
> Allows the call to succeed, potentially before the entry is fully open and available, implying that subsequent calls to the entry might return an error.
    
MAPI_GAL_ONLY
  
> Uses only the GAL to perform name resolution. This flag is supported only by the Exchange address book provider.
    
MAPI_MODIFY
  
> Requests that the entry be opened with read and write permission. Because entries are opened with read-only access by default, clients should not assume that read and write permission was granted regardless of whether MAPI_MODIFY is set.
    
MAPI_NO_CACHE
  
> Does not use the offline address book to perform name resolution. This flag is supported only by the Exchange address book provider.
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened entry.
    
 _lppUnk_
  
> [out] A pointer to a pointer of the opened entry.
    

