---
title: "IAddrBookPrepareRecips"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.PrepareRecips
api_type:
- COM
ms.assetid: d423f7b5-23b8-44dd-bca3-6590182dc42d
description: "Last modified: July 23, 2011"
---

# IAddrBook::PrepareRecips

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Prepares a recipient list for later use by the messaging system. 
  
```cpp
HRESULT PrepareRecips(
  ULONG ulFlags,
  LPSPropTagArray lpSPropTagArray,
  LPADRLIST lpRecipList
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how the entry is opened. The following flag can be set:
    
MAPI_CACHE_ONLY
  
> Use only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and to access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider.
    
 _lpSPropTagArray_
  
> [in] A pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags that indicate the properties, if any, that require updating. The  _lpSPropTagArray_ parameter can be NULL. 
    
 _lpRecipList_
  
> [in] A pointer to an [ADRLIST](adrlist.md) structure that contains the list of recipients. 
    
## Return value

S_OK 
  
> The recipient list was successfully prepared.
    
## Remarks

Clients and service providers call the **PrepareRecips** method to do the following: 
  
- Ensure that all recipients in the _lpRecipList_ parameter have long-term entry identifiers. 
    
- Ensure that each recipient in the _lpRecipList_ parameter has the properties listed in the _lpSPropTagArray_ parameter and that these properties appear at the start of the recipient list. 
    
MAPI converts each recipient's short-term entry identifiers to long-term entry identifiers. If necessary, recipients' long-term entry identifiers are retrieved from the appropriate address book provider and any additional properties are requested.
  
In an individual recipient entry, the requested properties are ordered first, followed by any properties that were already present for the entry. If one or more of the requested properties in the _lpSPropTagArray_ parameter are not handled by the appropriate address book provider, their property types will be set to PT_ERROR. Their property values will be set to either to MAPI_E_NOT_FOUND or to another value that gives a more specific reason why the properties are not available. Each [SPropValue](spropvalue.md) structure included in the _lpRecipList_ parameter must be separately allocated by using the [MAPIAllocateBuffer](mapiallocatebuffer.md) and [MAPIAllocateMore](mapiallocatemore.md) functions so that it can be freed individually. 
  
For information about PT_ERROR, see [Property Types](property-types.md).
  
## See also



[ADRLIST](adrlist.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md)
  
[SPropValue](spropvalue.md)
  
[SRowSet](srowset.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

