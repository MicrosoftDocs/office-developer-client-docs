---
title: "IMsgStoreSetLockState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgStore.SetLockState
api_type:
- COM
ms.assetid: 4b1176ec-4126-43f5-856d-cbab8d622825
description: "Last modified: July 23, 2011"
---

# IMsgStore::SetLockState

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Locks or unlocks a message. This method is called only by the MAPI spooler.
  
```
HRESULT SetLockState(
  LPMESSAGE lpMessage,
  ULONG ulLockState  
);
```

## Parameters

 _lpMessage_
  
> [in] A pointer to the message to lock or unlock.
    
 _ulLockState_
  
> [in] A value that indicates whether the message should be locked or unlocked. One of the following values is valid:
    
MSG_LOCKED 
  
> The message should be locked. 
    
MSG_UNLOCKED 
  
> The message should be unlocked.
    
## Return value

S_OK 
  
> The lock state of the message was successfully set.
    
## Remarks

The **IMsgStore::SetLockState** method locks or unlocks a message. **SetLockState** can be called only by the MAPI spooler while it is sending the message. 
  
Usually, when the MAPI spooler calls **SetLockState** to lock a message, it locks only the oldest message (that is, the next message queued for the MAPI spooler to send). If the oldest message in the queue is waiting for a temporarily unavailable transport provider, and the next message in the queue uses a different transport provider, the MAPI spooler can begin processing the later message. It begins processing by locking that message by using **SetLockState**.
  
## Notes to Implementers

After the MAPI spooler has called **SetLockState** with the  _ulLockState_ parameter set to MSG_LOCKED, calls to the [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md) method to cancel the message's transmission must fail. 
  
Call the message's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method in your **SetLockState** implementation so that any changes that were made to the message before the **SetLockState** call was received are saved. 
  
## See also

#### Reference

[IMsgStore::AbortSubmit](imsgstore-abortsubmit.md)
  
[IMsgStore::FinishedMsg](imsgstore-finishedmsg.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)

