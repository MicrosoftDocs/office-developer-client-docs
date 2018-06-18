---
title: "IMessageSubmitMessage"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMessage.SubmitMessage
api_type:
- COM
ms.assetid: 9ce93469-c55d-48d1-9abb-a637716ed4f2
description: "Last modified: March 09, 2015"
---

# IMessage::SubmitMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Saves all of the message's properties and marks the message as ready to be sent.
  
```cpp
HRESULT SubmitMessage(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags used to control how a message is submitted. The following flag can be set:
    
FORCE_SUBMIT 
  
> MAPI should submit the message immediately. This flag is not currently in use.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_RECIPIENTS 
  
> The message's recipient table is empty.
    
## Remarks

The **IMessage::SubmitMessage** method marks a message as ready to be transmitted. MAPI passes messages to the underlying messaging system in the order in which they are marked for sending. Because of this functionality, a message might stay in a message store for some time before the underlying messaging system can take responsibility for it. The order of receipt at the destination is in the underlying messaging system's control and does not necessarily match the order in which messages were sent. 
  
## Notes to implementers

Call the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to save it and then check the message's **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property. If the MSGFLAG_RESEND flag is set, call [IMAPISupport::PrepareSubmit](imapisupport-preparesubmit.md). **PrepareSubmit** updates the recipient type and **PR_RESPONSIBILITY** ([PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property for all of the recipients in the resend message.
  
## Notes to callers

When **SubmitMessage** returns, all pointers to the message and its associated subobjects messages, folders, attachments, streams, tables, and so on are no longer valid. MAPI does not permit any further operations on these pointers, except for calling their **IUnknown::Release** methods. MAPI is designed such that after **SubmitMessage** is called, you should release the message and all associated subobjects. However, if **SubmitMessage** returns an error value indicating missing or invalid information, the message remains open and the pointers remain valid. 
  
To cancel a send operation, get and store a pointer to the message's **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property before the message is submitted. Because a message's entry identifier is invalidated after the message has been submitted, it is necessary to save it before calling **SubmitMessage**. To cancel the send, point the  _lpEntryId_ parameter to this entry identifier and call [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |**CFolderDlg::OnSubmitMessage** <br/> |MFCMAPI uses the **IMessage::SubmitMessage** method to submit the selected message.  <br/> |
   
## See also



[IMsgStore::AbortSubmit](imsgstore-abortsubmit.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

