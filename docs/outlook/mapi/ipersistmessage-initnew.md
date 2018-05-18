---
title: "IPersistMessageInitNew"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.InitNew
api_type:
- COM
ms.assetid: 4bf37c35-4f72-438a-912c-402f3711a5ea
description: "Last modified: July 23, 2011"
---

# IPersistMessage::InitNew

  
  
**Applies to**: Outlook 
  
Initializes a new message.
  
```
HRESULT InitNew(
  LPMAPIMESSAGESITE pMessageSite,
  LPMESSAGE pMessage
);
```

## Parameters

 _pMessageSite_
  
> [in] A pointer to the message site that the form will use to work with the message in the viewer.
    
 _pMessage_
  
> [in] A pointer to the new message.
    
## Return value

S_OK 
  
> The new message was successfully initialized.
    
## Remarks

Form viewers call the **IPersistMessage::InitNew** method when the user writes a new message that belongs to a message class that the form handles. If the form object has a valid user interface pointer, the user interface for the message object should be displayed. 
  
 **InitNew** should not be called when your form is in any state except the [Uninitialized](uninitialized-state.md) state. If the form is in one of the other states when **InitNew** is called, return E_UNEXPECTED. 
  
## Notes to Implementers

Typically, messages that have unsaved properties are marked as modified so that the client can display a dialog box that prompts the user whether these properties should be saved. If the user indicates that a message should be saved, save the data, mark the message as clean, and exit normally.
  
However, if processing for your newly initialized messages includes setting one or more computed properties, and it is important for those properties to be saved, do not mark the messages as modified. Because computed properties should be invisible to users, no dialog box should be displayed.
  
If your form has a reference to an active message site other than the one that is passed into **InitNew**, release the original site because it will no longer be used. Store the pointers to the message site and message from the  _pMessageSite_ and  _pMessage_ parameters and call both objects' [IUnknown::AddRef](http://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) methods to increment their reference counts. 
  
Set the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) and **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) properties for the new message to something appropriate for your message class. Many message classes, for example, set **PR_MESSAGE_FLAGS** to MSGFLAG_UNSENT for new messages. 
  
Before returning, transition the form to the [Normal](normal-state.md) state if no errors have occurred. Send a new message notification to all registered viewers by calling their [IMAPIViewAdviseSink::OnNewMessage](imapiviewadvisesink-onnewmessage.md) methods and return S_OK. 
  
## Notes to Callers

After you have made a successful call to **InitNew**, you can assume that the following required properties, and no others, have been set for the form:
  
 **PR_DELETE_AFTER_SUBMIT** ([PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md))
  
 **PR_IMPORTANCE** ([PidTagImportance](pidtagimportance-canonical-property.md))
  
 **PR_ORIGINATOR_DELIVERY_REPORT_REQUESTED** ([PidTagOriginatorDeliveryReportRequested](pidtagoriginatordeliveryreportrequested-canonical-property.md))
  
 **PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md))
  
 **PR_READ_RECEIPT_REQUESTED** ([PidTagReadReceiptRequested](pidtagreadreceiptrequested-canonical-property.md))
  
 **PR_SENSITIVITY** ([PidTagSensitivity](pidtagsensitivity-canonical-property.md))
  
 **PR_SENTMAIL_ENTRYID** ([PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md))
  
For more information about the states of forms, see [Form States](form-states.md). For more information about how storage objects are initialized, see the [IPersistStorage::InitNew](http://msdn.microsoft.com/library/79caf1f6-d974-4aee-8563-eda4876a0a90%28Office.15%29.aspx) method. 
  
## See also

#### Reference

[IPersistMessage : IUnknown](ipersistmessageiunknown.md)

