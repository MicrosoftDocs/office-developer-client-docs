---
title: "IABLogonPrepareRecips"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABLogon.PrepareRecips
api_type:
- COM
ms.assetid: 3c1845ea-e291-4855-9afd-51d2c64d7e85
description: "Last modified: July 23, 2011"
---

# IABLogon::PrepareRecips

  
  
**Applies to**: Outlook 
  
Prepares a recipient list for later use by the messaging system.
  
```
HRESULT PrepareRecips(
  ULONG ulFlags,
  LPSPropTagArray lpPropTagArray,
  LPADRLIST lpRecipList
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text in the returned strings. The following flag can be set:
    
MAPI_CACHE_ONLY
  
> Use only the offline address book to perform name resolution. For example, you can use this flag to allow a client application to open the global address list (GAL) in cached exchange mode and access an entry in that address book from the cache without creating traffic between the client and the server. This flag is supported only by the Exchange Address Book Provider.
    
 _lpPropTagArray_
  
> [in] A pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags that indicate the properties that require updating, if any. The  _lpPropTagArray_ parameter can be NULL. 
    
 _lpRecipList_
  
> [in] A pointer to an [ADRLIST](adrlist.md) structure that holds the recipient list. 
    
## Return value

S_OK 
  
> The recipient list was successfully prepared.
    
MAPI_E_NOT_FOUND 
  
> One or more of the recipients in the  _lpRecipList_ parameter do not exist. 
    
## Return value

A client calls the MAPI [IAddrBook::PrepareRecips](iaddrbook-preparerecips.md) method to modify or rearrange a set of properties for one or more recipients. The recipients may or may not be part of the recipient list of an outgoing message. MAPI transfers this call to an address book provider's **IABLogon::PrepareRecips** method. 
  
 **IABLogon::PrepareRecips** performs four main tasks: 
  
- Ensures that all recipients in the address list pointed to by the  _lpRecipList_ parameter have a long-term entry identifier. 
    
- Ensures that all recipients have the properties specified in the property value array pointed to by the  _lpPropTagArray_ parameter. 
    
- Ensures that the properties from the property value array appear before any other properties that existed before the call.
    
- Ensures that the order of the properties in each recipient's [ADRENTRY](adrentry.md) structure in the **ADRLIST** structure is the same as in the property value array. 
    
The **ADRENTRY** structure in the  _lpRecipList_ parameter contains one **ADRENTRY** structure for each recipient. Each **ADRENTRY** structure contains an array of [SPropValue](spropvalue.md) structures to describe the recipient's properties. When **IABLogon::PrepareRecips** returns, the **SPropValue** structure array for each recipient includes the properties from the  _lpPropTagArray_ followed by the other properties for the recipient. 
  
## Notes to Implementers

Implementing **IABLogon::PrepareRecips** involves putting properties in a specific order, retrieving property values, and converting short-term entry identifiers to long-term entry identifiers. The properties that are requested in the  _lpPropTagArray_ parameter must be at the start of the property value array associated with each recipient's **ADRENTRY** structure in the  _lpRecipList_ parameter. If values for these properties do not exist, open the associated messaging user or distribution list by using its entry identifier and retrieve the missing property values. 
  
Allocate each **SPropValue** structure passed in  _lpRecipList_ separately so that the structures can be freed individually. If you must allocate additional space for any **SPropValue** structure, for example, to store the data for a string property, use the [MAPIAllocateBuffer](mapiallocatebuffer.md) function to allocate additional space for the full property value array. Use the [MAPIFreeBuffer](mapifreebuffer.md) function to free the original property value array, and then use the [MAPIAllocateMore](mapiallocatemore.md) function to allocate any additional memory that is required. 
  
To implement **IABLogon::PrepareRecips**, use the following procedure:
  
1. Check for entries in the  _lpPropTagArray_ parameter. If the property value array is empty, there is no work to do. Return a success value. 
    
2. Process each recipient in the  _lpRecipList_ parameter. There is one **ADRENTRY** structure member for each recipient in the list. Ignore the following types of recipients: 
    
  - Recipients without an entry identifier in the **rgPropVals** member of their **ADRENTRY** structure (that is, unresolved recipients). 
    
  - Recipients with an entry identifier that does not belong to your provider. These recipients will be passed to another address book provider.
    
3. Open the recipient and retrieve the properties that are already set for the recipient.
    
4. Merge the property value array specified in the  _lpRecipList_ with the array of properties returned from **GetProps**. If the same property occurs in both property arrays, use the value from  _lpRecipList_.
    
5. If the  _lpRecipList_ property value array is big enough to hold all of the necessary properties, just replace it with the merged array. If the  _lpRecipList_ property value array is not big enough, replace it with a newly allocated array. Be sure the new array has an updated value in each of its **cValues** members. 
    
6. If you do not recognize one or more of the properties in the  _lpPropTagArray_ parameter, set the property type in the recipient's **ADRENTRY** structure to PT_ERROR and the property value either to MAPI_E_NOT_FOUND or to another value that gives a more specific reason for the unavailability of the property. For information about PT_ERROR, see [Property Types](property-types.md).
    
> [!NOTE]
> Never reallocate the **ADRLIST** structure that is passed into **IABLogon::PrepareRecips** or change its number of entries. 
  
## See also

#### Reference

[ADRLIST](adrlist.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md)
  
[SPropValue](spropvalue.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

