---
title: "IABContainerResolveNames"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IABContainer.ResolveNames
api_type:
- COM
ms.assetid: 27474af2-29a2-4cfb-b94f-72eb91562dac
---

# IABContainer::ResolveNames

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs name resolution for one or more recipient entries.
  
```cpp
HRESULT ResolveNames(
  LPSPropTagArray lpPropTagArray,
  ULONG ulFlags,
  LPADRLIST lpAdrList,
  LPFlagList lpFlagList
);
```

## Parameters

 _lpPropTagArray_
  
> [in] A pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags describing the properties to be included in the [ADRLIST](adrlist.md) structure returned by the provider. To request the provider's default set of properties, pass NULL in the _lpPropTagArray_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text in the returned strings. The following flags can be set:
    
EMS_AB_ADDRESS_LOOKUP
  
> Only exact proxy address matches will be found; partial matches are ignored. This flag is supported only by the Exchange Address Book Provider.
    
MAPI_CACHE_ONLY
  
> Only the offline address book will be used to perform name resolution. For example, you can use this flag to enable a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider. 
    
MAPI_UNICODE 
  
> The returned string properties are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lpAdrList_
  
> [in, out] On input, a pointer to an **ADRLIST** structure that contains the list of recipients to be resolved. On output, a pointer to an **ADRLIST** structure that contains the resolved names. 
    
 _lpFlagList_
  
> [in, out] A pointer to an array of flags, each flag corresponding to an [ADRENTRY](adrentry.md) structure in the _lpAdrList_ parameter, that provides the status of the name resolution operation for the recipient. The flags in the _lpFlagList_ parameter are in the same order as the entries in  _lpAdrList_. The following flags can be set:
    
MAPI_AMBIGUOUS 
  
> The corresponding recipient has been resolved, but not to a unique entry identifier. Other containers should not try to resolve this recipient. 
    
MAPI_RESOLVED 
  
> The corresponding recipient has been resolved to a unique entry identifier. Other containers should not try to resolve this recipient. 
    
MAPI_UNRESOLVED 
  
> The corresponding entry has not been resolved. Other containers should try to resolve this recipient.
    
## Return value

S_OK 
  
> The name resolution process was successful.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_NO_SUPPORT 
  
> The address book provider does not support bulk name resolution by using this method.
    
## Remarks

The **ResolveNames** method attempts to match unresolved recipients from the array of entries in the _lpAdrList_ parameter to recipients in this address book container. An unresolved recipient typically has only the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property and possibly a few other properties. An unresolved recipient does not have the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property, and its corresponding flag in the _lpFlagList_ parameter is set to MAPI_UNRESOLVED. Conversely, a resolved recipient always has at least the **PR_ENTRYID** property plus several other properties such as **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)), **PR_DISPLAY_NAME**, and **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)).
  
Name resolution typically starts when a client calls the [IAddrBook::ResolveName](iaddrbook-resolvename.md) method. Outlook MAPI responds by calling the **ResolveNames** method of each address book container included in the address book search path, specified by the **PR_AB_SEARCH_PATH** ([PidTagAbSearchPath](pidtagabsearchpath-canonical-property.md)) property. The entries in the _lpAdrList_ parameter include recipients already resolved because they are in containers for which MAPI has already called **ResolveNames**, because the entries appear earlier in the search path. 
  
Each container attempts to resolve the unresolved entries by matching the display name of the recipient with the display name of one of its entries. When a unique match is found, **ResolveNames** adds the **PR_ENTRYID** property and other properties that are included in the _lpPropTagArray_ parameter to the corresponding entry in the outgoing **ADRLIST** structure. **ResolveNames** then sets the entry in the _lpFlagList_ parameter to MAPI_RESOLVED. The entry identifier stored in the **PR_ENTRYID** property can be short-term or long-term. 
  
After all of the containers in the search path have attempted the name resolution process, MAPI opens a dialog box, if possible, to prompt the user for help in resolving any remaining conflicts. 
  
Clients can also use the returned **ADRLIST** structure in calls to the [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method. 
  
## Notes to implementers

You are not required to support name resolution with the **ResolveNames** method. Instead, or additionally, you can support it with the **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property restriction. If you decide to rely on the **PR_ANR** restriction for name resolution, you can return MAPI_E_NO_SUPPORT. For more information, see [Implementing Name Resolution](implementing-name-resolution.md).
  
Set a recipient's flag entry in the _lpFlagList_ parameter to MAPI_UNRESOLVED if the recipient does not match any of the container's recipients. 
  
When a recipient matches multiple recipients, set its flag to MAPI_AMBIGUOUS and do not change its **ADRENTRY** structure. 
  
MAPI requires certain properties for recipients that are included in a message's recipient list. You can include them in the **ADRENTRY** structure as part of the name resolution process or wait for MAPI to request them with calls to the [IAddrBook::PrepareRecips](iaddrbook-preparerecips.md) and [IMAPISupport::ExpandRecips](imapisupport-expandrecips.md) methods. You can eliminate these extra calls and improve performance by including the following properties in the **ADRENTRY** structures of all resolved recipients: 
  
- **PR_ADDRTYPE**
    
- **PR_DISPLAY_NAME**
    
- **PR_EMAIL_ADDRESS**
    
- **PR_ENTRYID**
    
- **PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))
    
- **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md))
    
- **PR_TRANSMITABLE_DISPLAY_NAME** ([PidTagTransmittableDisplayName](pidtagtransmittabledisplayname-canonical-property.md))
    
If some of the properties in the _lpPropTagArray_ parameter are unavailable—typically because the container entry does not support the properties and they are not included in the recipient's **ADRENTRY** member in the **ADRLIST** structure—set the property type of each unavailable property to PT_ERROR. 
  
Do not remove any properties from a resolved recipient's **ADRENTRY** structure. 
  
If you must replace rather than modify an **ADRENTRY** structure, free the original **ADRENTRY** structure first by calling the [MAPIFreeBuffer](mapifreebuffer.md) function, and then allocate the replacement **ADRENTRY** structure with [MAPIAllocateBuffer](mapiallocatebuffer.md).
  
## See also



[ADRENTRY](adrentry.md)
  
[ADRLIST](adrlist.md)
  
[IAddrBook::PrepareRecips](iaddrbook-preparerecips.md)
  
[IAddrBook::ResolveName](iaddrbook-resolvename.md)
  
[IMAPISupport::ExpandRecips](imapisupport-expandrecips.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[PidTagAnr Canonical Property](pidtaganr-canonical-property.md)
  
[SPropertyRestriction](spropertyrestriction.md)
  
[IABContainer : IMAPIContainer](iabcontainerimapicontainer.md)

