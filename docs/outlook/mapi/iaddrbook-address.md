---
title: "IAddrBookAddress"
description: Describes IAddrBookAddress provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.Address
api_type:
- COM
ms.assetid: ef2112c7-35cd-4106-ad18-a45e1dbe07d6
---

# IAddrBook::Address

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Displays the Outlook address book dialog box. 
  
```cpp
HRESULT Address(
  ULONG_PTR FAR * lpulUIParam,
  LPADRPARM lpAdrParms,
  LPADRLIST FAR * lppAdrList
);
```

## Parameters

 _lpulUIParam_
  
> [in, out] A pointer to a handle of the parent window of the dialog box. On input, a window handle must always be passed. On output, if the **ulFlags** member of the  _lpAdrParms_ parameter is set to DIALOG_SDI, the window handle of the modeless dialog box is returned. See Remarks. 
    
 _lpAdrParms_
  
> [in, out] A pointer to an [ADRPARM](adrparm.md) structure that controls the presentation and behavior of the address dialog box. 
    
 _lppAdrList_
  
> [in, out] A pointer to a pointer to an [ADRLIST](adrlist.md) structure that contains recipient information. On input, this parameter can be NULL or point to a valid pointer. On output, this parameter points to a pointer to valid recipient information. 
    
## Return value

S_OK 
  
> The common address dialog box was successfully displayed.
    
## Remarks

If the **ulFlags** member of the  _lpAdrParms_ parameter is set to DIALOG_SDI anticipating the return of the window handle of the modeless dialog box on output, it is ignored in Outlook; the modal version of the dialog is always shown in non-Outlook clients. 
  
The **ADRLIST** structure passed back by MAPI to the caller through the  _lppAdrList_ parameter contains an array of [ADRENTRY](adrentry.md) structures, one structure for each recipient. When passed to an outgoing message's [IMessage::ModifyRecipients](imessage-modifyrecipients.md) method in the _lpMods_ parameter, the **ADRLIST** structure can be used to update its recipient list. 
  
Each **ADRENTRY** structure in the **ADRLIST** structure contains zero or more [SPropValue](spropvalue.md) structures, one structure for every property set for the recipient. There can be zero **SPropValue** structures when the dialog box presented by the **Address** method is used to remove a recipient. When there are one or more **SPropValue** structures, the corresponding **ADRENTRY** structure is used to add or update a recipient. The recipient can be resolved, which indicates that one of the **SPropValue** structures describes the recipient's **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property, or unresolved, which indicates that the **PR_ENTRYID** property is missing. 
  
In addition to **PR_ENTRYID**, resolved recipients include the following properties:
  
- **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md))
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
The **ADRLIST** structure that the caller passes in might be a different size from the structure that MAPI returns. If MAPI must return a larger **ADRLIST** structure, it frees the original structure and allocates a new one. When you allocate memory for the **ADRLIST** structure, allocate the memory for each **SPropValue** structure separately. For more information about how to allocate and free **ADRLIST** structures, see [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md)
  
 **Address** returns immediately if the DIALOG_SDI flag is set in the **ulFlags** member of the **ADRPARM** structure in the _lpAdrParms_ parameter. The DIALOG_SDI flag is ignored for non-Outlook clients. If DIALOG_SDI is ignored, the modal version of the dialog will be displayed and a pointer to a handle should not be expected in  _lpulUIParam_.
  
 **Address** supports Unicode character strings in the **ADRPARM** structure if AB_UNICODEUI was specified in the **ulFlags** member of **ADRPARM** in the _lpAdrParms_ parameter, and it supports Unicode character strings in **ADRLIST**. The Unicode strings are converted to the multibyte character string (MBCS) format before they are displayed in the Outlook address book dialog box.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIStoreFunctions.cpp  <br/> |OpenOtherUsersMailboxFromGal  <br/> |MFCMAPI uses the **Address** method to allow the user to select which mailbox to open. |
   
## See also



[ADRENTRY](adrentry.md)
  
[ADRLIST](adrlist.md)
  
[ADRPARM](adrparm.md)
  
[FreePadrlist](freepadrlist.md)
  
[FreeProws](freeprows.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropValue](spropvalue.md)
  
[SRowSet](srowset.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

