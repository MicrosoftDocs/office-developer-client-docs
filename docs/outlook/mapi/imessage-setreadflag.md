---
title: "IMessageSetReadFlag"
description: "IMessageSetReadFlag sets or clears the MSGFLAG_READ flag in the PR_MESSAGE_FLAGS property of the message and manages the sending of read reports."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMessage.SetReadFlag
api_type:
- COM
ms.assetid: 2d02ebf6-bb8b-42bb-9bd0-870dbae9aeb4
---

# IMessage::SetReadFlag

**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of the message and manages the sending of read reports.
  
```cpp
HRESULT SetReadFlag(
  ULONG ulFlags
);
```

## Parameters

_ulFlags_
  
> [in] Bitmask of flags that controls the setting of a message's read flag that is, the message's MSGFLAG_READ flag in its **PR_MESSAGE_FLAGS** property and the processing of read reports. The following flags can be set: 
    
  - CLEAR_READ_FLAG: The MSGFLAG_READ flag should be cleared in **PR_MESSAGE_FLAGS** and no read report should be sent. 
      
  - CLEAR_NRN_PENDING: The MSGFLAG_NRN_PENDING flag should be cleared in **PR_MESSAGE_FLAGS** and a non-read report should not be sent. 
      
  - CLEAR_RN_PENDING: The MSGFLAG_RN_PENDING flag should be cleared in **PR_MESSAGE_FLAGS** and no read report should be sent. 
      
  - GENERATE_RECEIPT_ONLY: A read report should be sent if one is pending, but there should be no change in the state of the MSGFLAG_READ flag.
      
  - MAPI_DEFERRED_ERRORS: Allows **SetReadFlag** to return successfully, possibly before the operation has completed. 
      
  - SUPPRESS_RECEIPT: A pending read report should be canceled if a read report had been requested and this call changes the state of the message from unread to read. If this call does not change the state of the message, the message store provider can ignore this flag.
    
## Return value

S_OK 
  
> The message's read flag has been successfully set or cleared.
    
MAPI_E_NO_SUPPRESS 
  
> The message store provider does not support the suppression of read reports.
    
MAPI_E_INVALID_PARAMETER 
  
> One of the following combinations of flags is set in the _ulFlags_ parameter: 
    
   - SUPPRESS_RECEIPT | CLEAR_READ_FLAG 
    
   - SUPPRESS_RECEIPT | CLEAR_READ_FLAG | GENERATE_RECEIPT_ONLY
    
   - CLEAR_READ_FLAG | GENERATE_RECEIPT_ONLY
    
## Remarks

The **IMessage::SetReadFlag** method sets or clears the message's MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** property and calls [IMAPIProp::SaveChanges](imapiprop-savechanges.md) to save the message. Setting the MSGFLAG_READ flag marks a message as having been read, which does not necessarily indicate that the intended recipient has actually read the message. 
  
**SetReadFlags** also manages the sending of read reports. A read report is sent only if the sender has requested one. 
  
The read flag cannot be altered for:
  
- Messages that do not exist.
    
- Messages that have been moved elsewhere.
    
- Messages that are open with read/write permission.
    
- Messages that are currently submitted.
    
## Notes to callers

If none of the flags are set in the _ulFlags_ parameter, the following rules apply: 
  
- If MSGFLAG_READ is already set, do nothing.
    
- If MSGFLAG_READ is not set, set it and send any pending read reports if the **PR_READ_RECEIPT_REQUESTED** ([PidTagReadReceiptRequested](pidtagreadreceiptrequested-canonical-property.md)) property is set.
    
If both the SUPPRESS_RECEIPT and GENERATE_RECEIPT_ONLY flags are set, the PR_READ_RECEIPT_REQUESTED bit, if set, should be cleared and a read report should not be sent.
  
When the SUPPRESS_RECEIPT flag is set:
  
- If MSGFLAG_READ is already set, do nothing. 
    
- If MSGFLAG_READ is not set, set it and cancel any pending read reports.
    
When the CLEAR_READ_FLAG flag is set, clear the MSGFLAG_READ flag in each message's **PR_MESSAGE_FLAGS** property and do not send any read reports. 
  
When the GENERATE_RECEIPT_ONLY flag is set, send any pending read reports. Do not set or clear MSGFLAG_READ.
  
When both the SUPPRESS_RECEIPT and GENERATE_RECEIPT_ONLY flags are set, set the PR_READ_RECEIPT_REQUESTED property to FALSE if it is set and do not send a read report.
  
You can optimize report behavior by suppressing the generation of read reports under certain conditions. However, if you do not support the suppression of reports and a client calls **SetReadFlag** with the SUPPRESS_RECEIPT flag set, return MAPI_E_NO_SUPPRESS. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolderDlg::OnSetReadFlag  <br/> |MFCMAPI uses the **IMessage::SetReadFlag** method to set read flags on selected messages. |
   
## See also

- [IMAPIContainer::OpenEntry](imapicontainer-openentry.md)  
- [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md)  
- [IMAPIProp::GetProps](imapiprop-getprops.md)  
- [IMAPIProp::SaveChanges](imapiprop-savechanges.md) 
- [PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md) 
- [IMessage : IMAPIProp](imessageimapiprop.md)
- [MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

