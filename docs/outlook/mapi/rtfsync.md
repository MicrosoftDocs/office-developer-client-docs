---
title: "RTFSync"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- RTFSync
api_type:
- HeaderDef
ms.assetid: 627f95e9-39ac-4d43-8f02-687783b09785
description: "Last modified: March 09, 2015"
---

# RTFSync

**Applies to**: Outlook 
  
Makes sure that the Rich Text Format (RTF) message text matches the plain text version. It is necessary to call this function before reading the RTF version and after modifying the RTF version. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |RTF-aware client applications and message store providers  <br/> |
   
```cpp
HRESULT RTFSync(
  LPMESSAGE lpMessage,
  ULONG ulFlags,
  BOOL FAR * lpfMessageUpdated
);
```

## Parameters

_lpMessage_
  
> [in] Pointer to the message to be updated.
    
_ulFlags_
  
> [in] Bitmask of flags used to indicate the RTF or plain text version of the message has changed. The following flags can be set:
    
  - RTF_SYNC_BODY_CHANGED: The plain text version of the message has changed.
      
  - RTF_SYNC_RTF_CHANGED: The RTF version of the message has changed.
    
  All other bits in the  _ulFlags_ parameter are reserved for future use. 
    
_lpfMessageUpdated_
  
> [out] Pointer to a variable indicating whether there is an updated message. TRUE if there is an updated message, FALSE otherwise.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

If the **PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md)) property is missing or is FALSE, before reading the **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property the **RTFSync** function should be called with the RTF_SYNC_BODY_CHANGED flag set. 
  
If the STORE_RTF_OK flag is not set in the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property, this function should be called with the RTF_SYNC_RTF_CHANGED flag set after modifying **PR_RTF_COMPRESSED**. 
  
If both **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) and **PR_RTF_COMPRESSED** have been changed, the **RTFSync** function should be called with both flags set. 
  
If the value of the  _lpfMessageUpdated_ parameter is set to TRUE, then the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method should be called for the message. If **SaveChanges** is not called, the modifications will not be saved in the message. 
  
Message store providers can use **RTFSync** to keep the **PR_BODY** and **PR_RTF_COMPRESSED** properties synchronized. 
  
For more information, see [Supporting RTF Text for Message Store Providers](supporting-rtf-text-for-message-store-providers.md). 
  
## See also

- [WrapCompressedRTFStream](wrapcompressedrtfstream.md)

