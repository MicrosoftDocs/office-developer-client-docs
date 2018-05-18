---
title: "IMAPISupportDoSentMail"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.DoSentMail
api_type:
- COM
ms.assetid: 4bb65c2a-9926-42da-9161-47836e8de40a
description: "Last modified: July 23, 2011"
---

# IMAPISupport::DoSentMail

  
  
**Applies to**: Outlook 
  
Processes a sent message.
  
```cpp
HRESULT DoSentMail(
  ULONG ulFlags,
  LPMESSAGE lpMessage
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpMessage_
  
> [in] A pointer to the open message for which a message should be generated in the folder designated to hold sent items.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

The **IMAPISupport::DoSentMail** method is implemented for message store provider support objects. Message store providers call **DoSentMail** from their implementation of the [IMsgStore::FinishedMsg](imsgstore-finishedmsg.md) method, which is called by the MAPI spooler when it has finished processing a message. **FinishedMsg** unlocks the message, ensures that the message's reference count is 1, and calls **DoSentMail**.
  
 **DoSentMail** performs the following tasks: 
  
- Checks the message for the **PR_DELETE_AFTER_SUBMIT** ([PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md)) property to determine whether the message should be deleted after sending.
    
- Determines the location of the Sent Items folder.
    
- Initiates message hook processing for any hooks set on the Sent Items folder.
    
- Moves the message to the Sent Items folder, Deleted Items folder, or to another folder.
    
- Releases the message.
    
## See also



[IMsgStore::FinishedMsg](imsgstore-finishedmsg.md)
  
[PidTagDeleteAfterSubmit Canonical Property](pidtagdeleteaftersubmit-canonical-property.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

