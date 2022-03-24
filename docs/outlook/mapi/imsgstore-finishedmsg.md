---
title: "IMsgStoreFinishedMsg"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.FinishedMsg
api_type:
- COM
ms.assetid: c32493fa-aa42-485b-9ea4-f93b835906df
description: "Last modified: March 09, 2015"
---

# IMsgStore::FinishedMsg

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables the message store provider to perform processing on a sent message. This method is called only by the MAPI spooler.
  
```cpp
HRESULT FinishedMsg(
  ULONG ulFlags,
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the message to be processed.
    
## Return value

S_OK 
  
> Processing on the sent message was successful.
    
MAPI_E_NO_SUPPORT 
  
> The message store provider does not support sent message processing. This error value is returned if the caller is not the MAPI spooler.
    
## Remarks

The **IMsgStore::FinishedMsg** method performs processing on a sent message. This processing can involve deleting the message, moving it to a different folder, or both actions. The type of processing depends on whether the **PR_DELETE_AFTER_SUBMIT** ([PidTagDeleteAfterSubmit](pidtagdeleteaftersubmit-canonical-property.md)) and **PR_SENTMAIL_ENTRYID** ([PidTagSentMailEntryId](pidtagsentmailentryid-canonical-property.md)) properties are set. 
  
## Notes to implementers

In your implementation of **FinishedMsg**, unlock the message identified by  _lpEntryID_ and perform the appropriate processing. The target message will always be locked; the MAPI spooler never passes the entry identifier for an unlocked message to **FinishedMsg**.
  
It is possible that neither **PR_DELETE_AFTER_SUBMIT** or **PR_SENTMAIL_ENTRYID** is set, both are set, or one or the other is set. The following table describes the action you should take based on the settings: 
  
|Property|Description|
|:-----|:-----|
|If neither property is set:  <br/> |Leave the message in the folder from which it was sent (typically the Outbox). |
|If both properties are set:  <br/> |Move the message to the indicated folder, if desired, and then delete it. |
|If PR_SENTMAIL_ENTRYID is set:  <br/> |Move the message to the indicated folder. |
|If PR_DELETE_AFTER_SUBMIT is set:  <br/> |Delete the message. |
   
After you have taken whatever action is appropriate, call the [IMAPISupport::DoSentMail](imapisupport-dosentmail.md) method. 
  
## See also



[IMAPISupport::DoSentMail](imapisupport-dosentmail.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)

