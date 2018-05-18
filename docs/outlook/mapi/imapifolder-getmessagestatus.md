---
title: "IMAPIFolderGetMessageStatus"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.GetMessageStatus
api_type:
- COM
ms.assetid: 3ddbb129-5d6b-4eca-aba0-3620609ed0c1
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::GetMessageStatus

  
  
**Applies to**: Outlook 
  
Obtains the status associated with a message in a particular folder (for example, whether that message is marked for deletion).
  
```cpp
HRESULT GetMessageStatus(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulFlags,
  ULONG FAR * lpulMessageStatus
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for the message whose status is obtained.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulMessageStatus_
  
> [out] A pointer to a pointer to a bitmask of flags that indicate the message's status. Bits 0 through 15 are reserved and must be zero; bits 16 through 31 are available for implementation-specific use. The following flags can be set:
    
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
    
## Return value

S_OK 
  
> The message status was successfully retrieved.
    
## Remarks

The **IMAPIFolder::GetMessageStatus** method returns the status of a message. Message status is stored in the message's **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property. 
  
## Notes to implementers

How the message status bits are set, cleared, and used depends completely on your implementation, except that bits 0 through 15 are reserved and must be zero. If you store messages in the IPM subtree, MAPI reserves bits 16 through 31 for use by IPM clients. If you store messages in other subtrees, you can use bits 16 through 31 for your own purposes.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::GetNextMessage  <br/> |MFCMAPI uses the **IMAPIFolder::GetMessageStatus** method to get the status of the next message to be displayed.  <br/> |
|MAPIFormFunctions.cpp  <br/> |OpenMessageNonModal and OpenMessageModal  <br/> |MFCMAPI uses the **IMAPIFolder::GetMessageStatus** method to get the status of the message to be displayed to pass to the form viewer, which is either CMyMAPIFormViewer or [IMAPISession::ShowForm](imapisession-showform.md).  <br/> |
   
## See also



[IMAPIFolder::SetMessageStatus](imapifolder-setmessagestatus.md)
  
[IMAPISession::ShowForm](imapisession-showform.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

