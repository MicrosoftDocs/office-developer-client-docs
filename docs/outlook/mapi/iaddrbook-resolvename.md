---
title: "IAddrBookResolveName"
description: The IAddrBookResolveName function performs name resolution, assigning entry identifiers to recipients in a recipient list.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.ResolveName
api_type:
- COM
ms.assetid: a7823c16-efda-45c2-b931-3e1fbc823b0b
---

# IAddrBook::ResolveName

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs name resolution, assigning entry identifiers to recipients in a recipient list.
  
```cpp
HRESULT ResolveName(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPSTR lpszNewEntryTitle,
  LPADRLIST lpAdrList
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of a dialog box that is shown, if specified, to prompt the user to resolve ambiguity.
    
 _ulFlags_
  
> [in] A bitmask of flags that control various aspects of the resolution process. The following flags can be set:
    
AB_UNICODEUI
  
> Indicates that  _lpszNewEntryTitle_ is a UNICODE string. 
    
MAPI_CACHE_ONLY
  
> Use only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider.
    
MAPI_DIALOG 
  
> Displays a dialog box to prompt the user for additional name resolution information. If this flag is not set, no dialog box is displayed. 
    
MAPI_UNICODE 
  
> Indicates that the properties returned in the address list should be of type PT_UNICODE instead of PT_STRING8. 
    
 _lpszNewEntryTitle_
  
> [in] A pointer to text for the title of the control in the dialog box that prompts the user to enter a recipient. The title varies depending on the type of recipient. The  _lpszNewEntryTitle_ parameter can be NULL. 
    
 _lpAdrList_
  
> [in-out] A pointer to an [ADRLIST](adrlist.md) structure that contains the list of recipient names to be resolved. This **ADRLIST** structure can be created by the [IAddrBook::Address](iaddrbook-address.md) method. 
    
## Return value

S_OK 
  
> The name resolution process succeeded.
    
MAPI_E_AMBIGUOUS_RECIP 
  
> At least one recipient in the _lpAdrList_ parameter matched more than one entry in the address book. Usually, this value is returned when the MAPI_DIALOG flag is set, prohibiting the display of a dialog box. 
    
MAPI_E_NOT_FOUND 
  
> At least one recipient in the _lpAdrList_ parameter cannot be resolved. Usually, this value is returned when the MAPI_DIALOG flag is set, prohibiting the display of a dialog box. 
    
## Remarks

Clients and service providers call the **ResolveName** method to initiate the name resolution process. An unresolved entry is an entry that does not yet have an entry identifier or **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
  
 **ResolveName** goes through the following process for each unresolved entry in the address list passed in the _lpAdrList_ parameter. 
  
1. If the address type of the recipient adheres to the format of an SMTP address ( _displayname_@ _domain.top-level-domain_), **ResolveName** assigns it a one-off entry identifier. 
    
2. For each container in the **PR_AB_SEARCH_PATH** ([PidTagAbSearchPath](pidtagabsearchpath-canonical-property.md)) property, **ResolveName** calls the [IABContainer::ResolveNames](iabcontainer-resolvenames.md) method. **ResolveNames** tries to match the display name of each unresolved recipient with a display name that belongs to one of its entries. 
    
3. If a container does not support **ResolveNames**, **ResolveName** restricts the container's contents table by using a **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property restriction. This restriction causes the container to perform a "best guess" type of search to locate a matching recipient. All containers must support the **PR_ANR** property restriction. 
    
4. When a container returns a recipient that matches multiple names, **ResolveName** displays a dialog box if the MAPI_DIALOG flag is set, which lets the user select the correct name. 
    
5. If all of the containers in the **PR_AB_SEARCH_PATH** property have been called and no match has been found, the recipient remains unresolved. 
    
If one or more recipients are unresolved, **ResolveName** returns MAPI_E_NOT_FOUND. If one or more recipients had ambiguous resolution that could not be resolved with a dialog box, or because the MAPI_DIALOG flag was not set, **ResolveName** returns MAPI_E_AMBIGUOUS_RECIP. When some of the recipients are ambiguous and some cannot be resolved, **ResolveName** can return either error value. 
  
If a name cannot be resolved, the client can create a one-off address that has a specially formatted address and entry identifier. For more information about the format of one-off entry identifiers, see [One-Off Entry Identifiers](one-off-entry-identifiers.md). For more information about the format of one-off addresses, see [One-Off Addresses](one-off-addresses.md).
  
MAPI supports Unicode character strings for the **ADRLIST** and the new entry title parameters to **ResolveName**; if you set the MAPI_UNICODE flag, the following properties are returned as type PT_UNICODE in the [ADRENTRY](adrentry.md) structures: 
  
- **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))
    
- **PR_TRANSMITABLE_DISPLAY_NAME** ([PidTagTransmittableDisplayName](pidtagtransmittabledisplayname-canonical-property.md))
    
However, the **PR_7BIT_DISPLAY_NAME** ([PidTag7BitDisplayName](pidtag7bitdisplayname-canonical-property.md)) property is always returned as type PT_STRING8.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIABFunctions.cpp  <br/> |AddOneOffAddress  <br/> |MFCMAPI uses the **ResolveName** method to resolve a one-off address before adding it to a message. |
|MAPIABFunctions.cpp  <br/> |AddRecipient  <br/> |MFCMAPI uses the **ResolveName** method to look up an address book entry by display name. |
   
## See also



[ADRLIST](adrlist.md)
  
[IABContainer::ResolveNames](iabcontainer-resolvenames.md)
  
[IAddrBook::Address](iaddrbook-address.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

