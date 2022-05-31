---
title: "HrOpenABEntryWithExchangeContext" 
description: This article describes HrOpenABEntryWithExchangeContext which opens the entryID using the Exchange Address Book identified by pEmsmdbUID.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: b640a5aa-4e36-4983-bf11-9428809e830b
---

# HrOpenABEntryWithExchangeContext

**Applies to**: Outlook 2013 | Outlook 2016
 
Opens the **entryID** using the Exchange Address Book identified by **pEmsmdbUID**. This function works similarly to [IAddrBook::Details](iaddrbook-details.md) except that using this function ensures that the [IAddrBook::OpenEntry](iaddrbook-openentry.md) is opened by using the expected Exchange Address Book Provider.
 
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
HRESULT HrDoABDetailsWithExchangeContext(
  LPMAPISESSION pmsess,
  const MAPIUID *pEmsmdbUID,
  LPADRBOOK pAddrBook,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID lpInterface,
  ULONG ulFlags
);
```

## Parameters

 _pmsess_
  
> [in] The logged on **IMAPISession**. It cannot be NULL.

 _pEmsmdbUID_
  
> [in] A pointer to an **emsmdbUID** that identifies the Exchange Service that contains the Exchange Address Book Provider that this function should use to display details on the entry identifier. If the incoming entry identifier is not an Exchange Address Book Provider entry identifier, this parameter is ignored and the function call behaves like [IAddrBook::Details](iaddrbook-details.md). If this parameter is NULL or a zero MAPIUID, this function behaves like [IAddrBook::Details](iaddrbook-details.md).

 _pAddrBook_
  
> [in] The address book used to open the entry identifier. It cannot be NULL.

 _cbEntryID_
  
> [in] The byte count of the entry identifier specified by the _lpEntryID_ parameter.

 _lpEntryID_
  
> [in] A pointer to the entry identifier that represents the address book entry to open.

 _ulFlags_
  
> [in] A bitmask of flags that controls how the entry is opened. The following flags can be set:

MAPI_BEST_ACCESS
  
> Requests that the entry be opened with the maximum allowed network and client permissions. For example, if the client has read and write permission, the address book provider attempts to open the entry with read and write permission. The client can retrieve the access level that was granted by calling the [IMAPIProp::GetProps](imapiprop-getprops.md) method of the open entry and retrieving the PR_ACCESS_LEVEL (PidTagAccessLevel) property.

MAPI_CACHE_ONLY
  
> Uses only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider.

MAPI_DEFERRED_ERRORS
  
> Allows the call to succeed, potentially before the entry is fully open and available, implying that subsequent calls to the entry might return an error.

MAPI_GAL_ONLY
  
> Uses only the GAL to perform name resolution. This flag is supported only by the Exchange Address Book Provider.

MAPI_MODIFY
  
> Requests that the entry be opened with read and write permission. Because entries are opened with read-only access by default, clients should not assume that read and write permission was granted regardless of whether MAPI_MODIFY is set.

MAPI_NO_CACHE
  
> Does not use the offline address book to perform name resolution. This flag is supported only by the Exchange Address Book Provider.
