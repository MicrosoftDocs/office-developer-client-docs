---
title: "IAddrBookOpenEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.OpenEntry
api_type:
- COM
ms.assetid: bd7746f4-8070-4cc5-8b8e-c527c5847545
description: "Last modified: February 01, 2013"
---

# IAddrBook::OpenEntry

  
  
**Applies to**: Outlook 
  
Opens an address book entry and returns a pointer to an interface that can be used to access the entry.
  
```
HRESULT OpenEntry(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier that represents the address book entry to open.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) of the interface to be used to access the open entry. Passing NULL returns the object's standard interface. For messaging users, the standard interface is [IMailUser : IMAPIProp](imailuserimapiprop.md). For distribution lists, it is [IDistList : IMAPIContainer](idistlistimapicontainer.md) and for containers, it is [IABContainer : IMAPIContainer](iabcontainerimapicontainer.md). Callers can set  _lpInterface_ to the appropriate standard interface or an interface in the inheritance hierarchy. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the entry is opened. The following flags can be set.
    
MAPI_BEST_ACCESS 
  
> Requests that the entry be opened with the maximum allowed network and client permissions. For example, if the client has read/write permission, the address book provider should attempt to open the entry with read/write permission. The client can retrieve the access level that was granted by calling the open entry's [IMAPIProp::GetProps](imapiprop-getprops.md) method and retrieving the **PR_ACCESS_LEVEL** ( [PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property.
    
MAPI_CACHE_ONLY
  
> Opens an address book entry and accesses it only from the cache. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange address book provider.
    
MAPI_DEFERRED_ERRORS 
  
> Allows the call to succeed, potentially before the entry is fully open and available, implying that later calls to the entry might return an error.
    
MAPI_GAL_ONLY
  
> Use only the GAL to perform name resolution. This flag is supported only by the Exchange Address Book Provider.
    
    > [!NOTE]
    > The  _ulFlags_ MAPI_GAL_ONLY might not be defined in the downloadable header file you currently have, in which case you can add it to your code using the following value: >  `#define MAPI_GAL_ONLY (0x00000080)`
  
MAPI_MODIFY 
  
> Requests that the entry be opened with read/write permission. Because entries are opened with read-only access by default, clients should not assume that read/write permission was granted regardless of whether MAPI_MODIFY is set.
    
MAPI_NO_CACHE
  
> Do not use the offline address book to perform name resolution. This flag is supported only by the Exchange Address Book Provider.
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened entry.
    
 _lppUnk_
  
> [out] A pointer to a pointer to the opened entry.
    
## Return value

S_OK 
  
> The entry was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to open an entry for which the user has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> The entry represented by  _lpEntryID_ does not exist. 
    
MAPI_E_UNKNOWN_ENTRYID 
  
> The entry identifier specified in  _lpEntryID_ is not recognized. This value is typically returned if the address book provider responsible for the corresponding entry is not open. 
    
## Remarks

Clients and service providers call the **IAddrBook::OpenEntry** method to open an address book entry. MAPI forwards the call to the appropriate address book provider, based on the [MAPIUID](mapiuid.md) structure included in the entry identifier passed in the  _lpEntryID_ parameter. The address book provider opens the entry as read-only unless the MAPI_MODIFY or MAPI_BEST_ACCESS flag in the  _ulFlags_ parameter is set. However, these flags are suggestions. If the address book provider does not allow modification for the entry requested, it returns MAPI_E_NO_ACCESS. 
  
The  _lpInterface_ parameter indicates which interface should be used to access the opened entry. Passing NULL in  _lpInterface_ indicates the standard MAPI interface for that type of entry should be used. Because the address book provider might return a different interface than the one suggested by the  _lpInterface_ parameter, the caller should check the value returned in the  _lpulObjType_ parameter to determine whether the object type returned is what was expected. If the object type is not of the type expected, the caller can cast the  _lppUnk_ parameter to a type that is more appropriate. 
  
## See also

#### Reference

[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

