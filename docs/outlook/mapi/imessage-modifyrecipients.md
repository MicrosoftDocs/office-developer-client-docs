---
title: "IMessageModifyRecipients"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMessage.ModifyRecipients
api_type:
- COM
ms.assetid: 2625f29d-325f-417d-bcec-49d580f9cd7e
description: "Last modified: March 09, 2015"
---

# IMessage::ModifyRecipients

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adds, deletes, or modifies message recipients.
  
```cpp
HRESULT ModifyRecipients(
  ULONG ulFlags,
  LPADRLIST lpMods
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags that controls the recipient changes. If zero is passed for the  _ulFlags_ parameter, **ModifyRecipients** replaces all existing recipients with the recipient list pointed to by the  _lpMods_ parameter. The following flags can be set for  _ulFlags_:
    
MODRECIP_ADD 
  
> The recipients pointed to by the  _lpMods_ parameter should be added to the recipient list. 
    
MODRECIP_MODIFY 
  
> The recipients pointed to by the  _lpMods_ parameter should replace existing recipients. All of the existing properties are replaced by those in the corresponding [ADRENTRY](adrentry.md) structure. 
    
MODRECIP_REMOVE 
  
> Existing recipients should be removed from the recipient list using as an index the **PR_ROWID** ([PidTagRowid](pidtagrowid-canonical-property.md)) property included in the property value array of each recipient entry in the  _lpMods_ parameter. 
    
 _lpMods_
  
> [in] Pointer to an [ADRLIST](adrlist.md) structure that contains a list of recipients to be added, deleted, or modified in the message. 
    
## Return value

S_OK 
  
> The recipient list was successfully modified.
    
## Remarks

The **IMessage::ModifyRecipients** method changes the message's recipient list. It is from this list, held in an [ADRLIST](adrlist.md) structure, that the recipient table is built. 
  
The **ADRLIST** structure contains one [ADRENTRY](adrentry.md) structure for each recipient and each **ADRENTRY** structure contains an array of property values describing the recipient properties. 
  
Recipients in the **ADRLIST** structure can be resolved or unresolved. The difference is in the number and type of properties that are included. An unresolved recipient contains only the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) and **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) properties while a resolved recipient contains those two properties plus **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) and **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)). If **PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) is available, it can be included also.
  
By the time a message is submitted, it must include only resolved recipients in its recipient list. Unresolved recipients cause nondelivery reports to be created and sent to the original sender of the message. For more information about the name resolution process from the client perspective, see [Resolving a Name](resolving-a-recipient-name.md). For more information from the perspective of the address book provider, see [Implementing Name Resolution](implementing-name-resolution.md).
  
In addition to resolved and unresolved recipients, a recipient can be NULL. The **cValues** member of the **ADRENTRY** structure for the recipient is set to zero and the **rgPropVals** member is set to NULL. 
  
## Notes to callers

You can create a recipient list by calling [IAddrBook::Address](imapisupport-address.md) to display the common dialog box and prompt the user to select entries. The address list pointed to by the  _lppAdrList_ parameter to **Address** can be passed to **ModifyRecipients** as the  _lpMods_ parameter. 
  
When you specify properties for a recipient in the [ADRLIST](adrlist.md) structure, include all of the recipient's properties, not only the new or changed ones. When a recipient is modified, any properties not included in the **ADRLIST** structure are deleted. To retrieve the current set of properties for all of a message's recipients, call [GetRecipientTable](imessage-getrecipienttable.md) and retrieve all of the rows. Because an **SRowSet** is identical in structure to an **ADRLIST**, you can use them interchangeably.
  
 **ModifyRecipients** replaces all of the entries in the current recipient list with the information pointed to by  _lpMods_ when none of the flags are set in the  _ulFlags_ parameter. 

When you set the MODRECIP_MODIFY flag, **ModifyRecipients** replaces each entire recipient row with the associated row in the [ADRLIST](adrlist.md) structure passed in  _lpMods_. Be careful to specify all of the properties that a recipient should have regardless of whether they have changed to prevent them from being unintentionally deleted.
  
Following are some rules for setting the properties of the recipients in the **ADRLIST** structure: 
  
- Do not use PT_NULL as a property type. **ModifyRecipients** returns an error when encountering this value. 
    
- Do not use PT_ERROR as a property type. **ModifyRecipients** ignores this value. 
    
- Include the **PR_ROWID** property for all recipients when you set either the MODRECIP_REMOVE or MODRECIP_MODIFY flag in  _ulFlags_. 
    
- Do not include the **PR_ROWID** property for any of the recipients when you set the MODRECIP_ADD flag in  _ulFlags_ or when you pass zero in  _ulFlags_.
    
If you include either the **PR_ADDRTYPE** property or **PR_EMAIL_ADDRESS** property for a recipient and one or both of these properties are inconsistent with the address type and address of the recipient as identified by **PR_ENTRYID**, the results are undefined. That is, there are three possibilities, depending on the service provider:
  
- The message will be delivered to the address described by the **PR_ADDRTYPE** and **PR_EMAIL_ADDRESS** properties. 
    
- The message will be delivered to the recipient identified by **PR_ENTRYID**.
    
- The message will be declared undeliverable due to the ambiguity of the address information.
    
Use the allocation rules outlined in [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md) to allocate memory for the recipient list. **ModifyRecipients** does not free the **ADRLIST** structure nor any of its substructures. The **ADRLIST** structure and each [SPropValue](spropvalue.md) structure must be separately allocated by using the [MAPIAllocateBuffer](mapiallocatebuffer.md) function such that each can be freed individually. If the method requires additional space for any **SPropValue** structure, it can replace the **SPropValue** structure with a new one that can later be freed using [MAPIFreeBuffer](mapifreebuffer.md). The original **SPropValue** structure should also be freed using **MAPIFreeBuffer**.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIABFunctions.cpp  <br/> |AddRecipient  <br/> |MFCMAPI uses the **IMessage::ModifyRecipients** method to add a new recipient to a message.  <br/> |
   
## See also



[ADRENTRY](adrentry.md)
  
[ADRLIST](adrlist.md)
  
[IAddrBook::Address](iaddrbook-address.md)
  
[IMAPISupport::Address](imapisupport-address.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropValue](spropvalue.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

