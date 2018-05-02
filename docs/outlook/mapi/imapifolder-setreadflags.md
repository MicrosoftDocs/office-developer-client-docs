---
title: "IMAPIFolderSetReadFlags"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.SetReadFlags
api_type:
- COM
ms.assetid: 95a40c8a-0a8b-46c7-a07a-cbc6a7de8a3c
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::SetReadFlags

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of one or more of the folder's messages, and manages the sending of read reports. 
  
```
HRESULT SetReadFlags(
  LPENTRYLIST lpMsgList,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _lpMsgList_
  
> [in] A pointer to an array of [ENTRYLIST](entrylist.md) structures that identify the message or messages that have read flags to set or clear. If  _lpMsgList_ is set to NULL, the read flags for all the folder's messages are set or cleared. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator. The  _ulUIParam_ parameter is ignored unless the MESSAGE_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using MAPI's implementation. The  _lpProgress_ parameter is ignored unless the MESSAGE_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the setting of a message's read flag and the processing of read reports. The following flags can be set:
    
CLEAR_READ_FLAG 
  
> The MSGFLAG_READ flag should be cleared in **PR_MESSAGE_FLAGS** and a read report should not be sent. 
    
CLEAR_NRN_PENDING 
  
> The MSGFLAG_NRN_PENDING flag should be cleared in **PR_MESSAGE_FLAGS** and an unread report should not be sent. 
    
CLEAR_RN_PENDING 
  
> The MSGFLAG_RN_PENDING flag should be cleared in **PR_MESSAGE_FLAGS** and a read report should not be sent. 
    
GENERATE_RECEIPT_ONLY 
  
> A read report should be sent if one is pending, but there should be no change in the state of the MSGFLAG_READ flag.
    
MAPI_DEFERRED_ERRORS 
  
> Allows **SetReadFlags** to return successfully, possibly before the operation has completed. 
    
MESSAGE_DIALOG 
  
> Displays a progress indicator while the operation proceeds.
    
SUPPRESS_RECEIPT 
  
> A pending read report should be canceled if a read report had been requested and this call changes the state of the message from unread to read. If this call does not change the state of the message, the message store provider can ignore this flag.
    
## Return value

S_OK 
  
> The read flag for the specified message or messages was successfully set or cleared.
    
MAPI_E_NO_SUPPRESS 
  
> The message store provider does not support the suppression of read reports.
    
MAPI_E_INVALID_PARAMETER 
  
> One of the following incompatible combinations of flags is set in the  _ulFlags_ parameter: 
    
    - SUPPRESS_RECEIPT | CLEAR_READ_FLAG 
    
    - SUPPRESS_RECEIPT | CLEAR_READ_FLAG | GENERATE_RECEIPT_ONLY
    
    - CLEAR_READ_FLAG | GENERATE_RECEIPT_ONLY
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all of the messages were successfully processed. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::SetReadFlags** method sets or clears the MSGFLAG_READ flag in the **PR_MESSAGE_FLAGS** property of one or more of the folder's messages. Setting the MSGFLAG_READ flag marks a message as read, which does not necessarily indicate that the intended recipient has actually read the message. 
  
 **SetReadFlags** also manages the sending of read reports. 
  
The read flag cannot be changed for the following:
  
- Messages that do not exist.
    
- Messages that have been moved elsewhere.
    
- Messages that are open with read/write permission.
    
- Messages that are currently submitted.
    
## Notes to Implementers

You can decide not to support the sending of read reports and the request to suppress read reports. To avoid suppressing a read report, return MAPI_E_NO_SUPPRESS when **SetReadFlags** is called with SUPPRESS_RECEIPT set in the  _ulFlags_ parameter. 
  
When the  _lpMsgList_ parameter points to more than one message, perform the operation as completely as possible for each message. Do not stop the operation prematurely unless a failure occurs that is beyond your control, such as running out of memory, running out of disk space, or corruption in the message store. 
  
If none of the flags are set in the  _ulFlags_ parameter, the following rules apply: 
  
- If MSGFLAG_READ is already set, do nothing.
    
- If MSGFLAG_READ is not set, set it immediately and send any pending read reports if the **PR_READ_RECEIPT_REQUESTED** ( [PidTagReadReceiptRequested](pidtagreadreceiptrequested-canonical-property.md)) property is set.
    
When the SUPPRESS_RECEIPT flag is set, the following rules apply:
  
- If MSGFLAG_READ is already set, do nothing. 
    
- If MSGFLAG_READ is not set, set it and cancel any pending read reports.
    
When the CLEAR_READ_FLAG flag is set, clear the MSGFLAG_READ flag in each message's **PR_MESSAGE_FLAGS** property and do not send any read reports. 
  
When the GENERATE_RECEIPT_ONLY flag is set, send any pending read reports. Do not set or clear MSGFLAG_READ.
  
When both the SUPPRESS_RECEIPT and GENERATE_RECEIPT_ONLY flags are set, set **PR_READ_RECEIPT_REQUESTED** to FALSE if it is set and do not send a read report. 
  
## Notes to Callers

Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**SetReadFlags** has successfully processed every message.  <br/> |S_OK  <br/> |
|**SetReadFlags** was unable to successfully process every message.  <br/> |MAPI_W_PARTIAL_COMPLETION or MAPI_E_NOT_FOUND  <br/> |
|**SetReadFlags** was unable to complete.  <br/> |Any error value except MAPI_E_NOT_FOUND  <br/> |
   
When **SetReadFlags** is unable to complete, do not assume that no work was done. **SetReadFlags** might have been able to set or clear the MSGFLAG_READ flag for one or more of the messages before encountering the error. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolderDlg::OnSetReadFlag  <br/> |MFCMAPI uses the **IMAPIFolder::SetReadFlags** method to manually set the read status on the specified messages.  <br/> |
   
## See also

#### Reference

[ENTRYLIST](entrylist.md)
  
[IMessage::SetReadFlag](imessage-setreadflag.md)
  
[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)
  
[PidTagReadReceiptRequested Canonical Property](pidtagreadreceiptrequested-canonical-property.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)

