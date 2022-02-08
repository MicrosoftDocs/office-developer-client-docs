---
title: "IMAPISupportAddress"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.Address
api_type:
- COM
ms.assetid: 8c22547e-ddf5-47f7-aed3-76e3854688df
description: "Last modified: July 23, 2011"
---

# IMAPISupport::Address

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Displays the common address dialog box. 
  
```cpp
HRESULT Address(
  ULONG_PTR FAR * lpulUIParam,
  LPADRPARM lpAdrParms,
  LPADRLIST FAR * lppAdrList
);
```

## Parameters

 _lpulUIParam_
  
> [in, out] A pointer to the handle of the parent window of the dialog box. On input, a window handle must always be passed. On output, if the DIALOG_SDI flag is set in the [ADRPARM](adrparm.md) structure pointed to by the  _lpAdrParms_ parameter, the window handle of the modeless dialog box is returned. 
    
 _lpAdrParms_
  
> [in, out] A pointer to an **ADRPARM** structure that controls the presentation and behavior of the address dialog box. 
    
 _lppAdrList_
  
> [in, out] A pointer to a pointer to an address list. On input, this list is either the current list of recipients in a message or NULL, if no such list exists. On output,  _lppAdrList_ points to an updated list of message recipients. 
    
## Return value

S_OK 
  
> The address dialog box was successfully displayed.
    
## Remarks

The **IMAPISupport::Address** method is implemented for address book provider support objects. Address book providers call **Address** to create or update a list of message recipients. 
  
Each recipient is described in an [ADRENTRY](adrentry.md) structure that is included in the [ADRLIST](adrlist.md) structure pointed to by the  _lppAdrList_ parameter. The **ADRENTRY** structure contains an array of recipient property values, one of which is the recipient's type, or **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) property. This **ADRLIST** structure can be passed to a client to use as the  _lpMods_ parameter in a call to [IMessage::ModifyRecipients](imessage-modifyrecipients.md).
  
Each recipient in the **ADRLIST** structure can be either resolved, which indicates that one of its property values is its **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property, or unresolved, which indicates that the **PR_ENTRYID** property is missing. 
  
In addition to **PR_ENTRYID**, resolved recipients include the following properties:
  
- **PR_RECIPIENT_TYPE**
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
Unresolved recipients typically include only **PR_DISPLAY_NAME** and **PR_RECIPIENT_TYPE**. 
  
## Notes to callers

The **ADRLIST** structure that the caller passes in might be a different size from the structure that MAPI returns. When you allocate memory for the **ADRLIST** structure, allocate the memory for each [SPropValue](spropvalue.md) structure separately. 
  
Use the pointers to the MAPI memory allocation functions passed in to your [ABProviderInit](abproviderinit.md) function to allocate memory. Allocate memory with the [MAPIAllocateBuffer](mapiallocatebuffer.md) function for **ADRLIST** and each property value structure in the **ADRENTRY** structures in **ADRLIST**. 
  
If **Address** must return a larger **ADRLIST** structure, or if you have passed NULL for  _lppAdrList_, **Address** frees the original structure and allocates a new one. **Address** also allocates additional property value structures in the **ADRLIST** structure and frees old ones as appropriate. For more information about how memory is managed for **ADRLIST** structures, see [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md).
  
 **Address** returns immediately if the DIALOG_SDI flag was set in the **ADRPARM** structure in the _lpAdrParms_ parameter. 
  
## See also



[ABProviderInit](abproviderinit.md)
  
[ADRENTRY](adrentry.md)
  
[ADRLIST](adrlist.md)
  
[ADRPARM](adrparm.md)
  
[FreePadrlist](freepadrlist.md)
  
[FreeProws](freeprows.md)
  
[IMAPISupport::GetMemAllocRoutines](imapisupport-getmemallocroutines.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagAddressType Canonical Property](pidtagaddresstype-canonical-property.md)
  
[PidTagDisplayName Canonical Property](pidtagdisplayname-canonical-property.md)
  
[PidTagDisplayType Canonical Property](pidtagdisplaytype-canonical-property.md)
  
[PidTagEntryId Canonical Property](pidtagentryid-canonical-property.md)
  
[PidTagRecipientType Canonical Property](pidtagrecipienttype-canonical-property.md)
  
[SPropValue](spropvalue.md)
  
[SRowSet](srowset.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)


[Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md)

