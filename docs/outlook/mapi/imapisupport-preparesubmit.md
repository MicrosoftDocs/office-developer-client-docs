---
title: "IMAPISupportPrepareSubmit" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.PrepareSubmit
api_type:
- COM
ms.assetid: 467242e3-96c9-4280-9cbc-9ecfe3f279cf
---

# IMAPISupport::PrepareSubmit

**Applies to**: Outlook 2013 | Outlook 2016

Prepares a message for submission to the MAPI spooler.

```cpp
HRESULT PrepareSubmit(
LPMESSAGE lpMessage,
ULONG FAR * lpulFlags
);
```

## Parameters

 _lpMessage_

> [in] A pointer to the message to prepare.

 _lpulFlags_

> [in, out] On input, the _lpulFlags_ parameter is reserved and must be zero. On output, _lpulFlags_ must be NULL.

## Return value

S_OK

> The message was successfully prepared.

## Remarks

The **IMAPISupport::PrepareSubmit** method is implemented for message store provider support objects. Message store providers call **PrepareSubmit** in their implementation of the [IMessage::SubmitMessage](imessage-submitmessage.md) method to prepare a message for submission to the MAPI spooler.

 **PrepareSubmit** is used to handle messages that have the MSGFLAG_RESEND flag set in their **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property. MSGFLAG_RESEND is set for messages that include a request to be resent when an initial transmission fails. **PrepareSubmit** determines which of the recipients in the recipient list successfully received the message and which did not.

To access the recipient list, **PrepareSubmit** calls the message's [IMessage::GetRecipientTable](imessage-getrecipienttable.md) method. To retrieve the recipient data, **PrepareSubmit** calls the recipient table's [IMAPITable::QueryRows](imapitable-queryrows.md) method. For each row in the table, **PrepareSubmit** checks the **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) property and takes one of the following actions:

- If the MAPI_SUBMITTED flag is set, **PrepareSubmit** clears the flag and sets the **PR_RESPONSIBILITY** ([PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property to FALSE.

- If the MAPI_SUBMITTED flag is not set, **PrepareSubmit** changes **PR_RECIPIENT_TYPE** to MAPI_P1 and sets **PR_RESPONSIBILITY** to TRUE.

## Notes to callers

Before you call **PrepareSubmit**, be sure you have called the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method and set the NOTIFY_READYTOSEND flag in the _ulFlags_ parameter. The **SpoolerNotify** call must be made once per session before the call to **PrepareSubmit**. **SpoolerNotify** synchronizes the MAPI spooler and ensures that all needed transport providers are logged on and their address types are registered.
 
## See also

[IMAPIFolder::GetMessageStatus](imapifolder-getmessagestatus.md)  
[IMessage::SubmitMessage](imessage-submitmessage.md)  
[IMAPISupport : IUnknown](imapisupportiunknown.md)
