---
title: "IMAPIFolderSetMessageStatus"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFolder.SetMessageStatus
api_type:
- COM
ms.assetid: 42ffbbe0-d678-474a-a016-91c71255613e
---

# IMAPIFolder::SetMessageStatus

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the status associated with a message (for example, whether that message is marked for deletion).
  
```cpp
HRESULT SetMessageStatus(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulNewStatus,
  ULONG ulNewStatusMask,
  ULONG FAR * lpulOldStatus
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for the message whose status is set.
    
 _ulNewStatus_
  
> [in] The new status to be assigned. 
    
 _ulNewStatusMask_
  
> [in] A bitmask of flags that is applied to the new status and indicates the flags to be set. The following flags can be set:
    
MSGSTATUS_DELMARKED 
  
> The message has been marked for deletion.
    
MSGSTATUS_HIDDEN 
  
> The message is not to be displayed.
    
MSGSTATUS_HIGHLIGHTED 
  
> The message is to be displayed highlighted.
    
MSGSTATUS_REMOTE_DELETE 
  
> The message has been marked for deletion at the remote message store without downloading to the local client.
    
MSGSTATUS_REMOTE_DOWNLOAD 
  
> The message has been marked for downloading from the remote message store to the local client.
    
MSGSTATUS_TAGGED 
  
> The message has been tagged for a client-defined purpose.
    
 _lpulOldStatus_
  
> [out] A pointer to the previous status of the message.
    
## Return value

S_OK 
  
> The message status was successfully set.
    
## Remarks

The **IMAPIFolder::SetMessageStatus** method sets the message status to the value that is stored in its **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property. 
  
## Notes to implementers

How the message status bits are set, cleared, and used depends completely on your implementation, except that bits 0 through 15 are reserved and must be zero. 
  
A remote transport provider's implementation of this method must follow the semantics described here. There are no special considerations. Clients use this method to set the MSGSTATUS_REMOTE_DOWNLOAD and MSGSTATUS_REMOTE_DELETE bits to indicate that a particular message is to be downloaded or deleted from the remote message store. A remote transport provider does not have to implement the related [IMAPIFolder::GetMessageStatus](imapifolder-getmessagestatus.md) method. Clients must look in the folder's contents table to determine the status of a message. 
  
## Notes to callers

You can use the **PR_MSG_STATUS** property of a message to negotiate a message lockout operation with other clients. Designate a bit as the lockout bit. To determine whether the lockout bit was set, examine the previous value for message status in the _lpulOldStatus_ parameter. Use the other bits in the _ulNewStatus_ parameter to track message status without interfering with the lockout bit. 
  
## See also



[IMAPIFolder::GetMessageStatus](imapifolder-getmessagestatus.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)

