---
title: "WrapStoreEntryID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- WrapStoreEntryID
api_type:
- HeaderDef
ms.assetid: b20107e3-5e23-4cde-9cd6-670c914ea70a
description: "Last modified: March 09, 2015"
---

# WrapStoreEntryID

  
  
**Applies to**: Outlook 
  
Converts a message store's internal entry identifier to an entry identifier more usable by the messaging system. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
WrapStoreEntryID(
  ULONG ulFlags,
  LPSTR szDLLName,
  ULONG cbOrigEntry,
  LPENTRYID lpOrigEntry,
  ULONG * lpcbWrappedEntry,
  LPENTRYID * lppWrappedEntry
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _szDLLName_
  
> [in] The name of the message store provider DLL. 
    
 _cbOrigEntry_
  
> [in] Size, in bytes, of the original entry identifier for the message store. 
    
 _lpOrigEntry_
  
> [in] Pointer to an [ENTRYID](entryid.md) structure that contains the original entry identifier. 
    
 _lpcbWrappedEntry_
  
> [out] Pointer to the size, in bytes, of the new entry identifier. 
    
 _lppWrappedEntry_
  
> [out] Pointer to a pointer to an **ENTRYID** structure that contains the new entry identifier. 
    
## Return value

None.
  
## Remarks

A message store object retains an internal entry identifier which is meaningful only to service providers coresident with that message store. For other messaging components, MAPI supplies a wrapped version of the internal entry identifier that makes it recognizable as that belong to the message store. Coresident service providers should always be given the original unwrapped message store entry identifier; client applications should always be given the wrapped version, which is then usable anywhere in the messaging domain and in other domains. 
  
A service provider can wrap a message store entry identifier using either the **WrapStoreEntryID** function or the [IMAPISupport::WrapStoreEntryID](imapisupport-wrapstoreentryid.md) method, which calls the **WrapStoreEntryID** function. The provider must wrap the entry identifier when exposing the message store's **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property or writing it into a profile section, and when exposing the **PR_STORE_ENTRYID** ( [PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md)) property. MAPI wraps a message store entry identifier when responding to an [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) call. 
  
When a client application passes a wrapped message store entry identifier to MAPI, for example in an [IMAPISession::OpenEntry](imapisession-openentry.md) call, MAPI unwraps the entry identifier before using it to call a provider method such as [IMSProvider::Logon](imsprovider-logon.md) or [IMSProvider::CompareStoreIDs](imsprovider-comparestoreids.md). 
  

