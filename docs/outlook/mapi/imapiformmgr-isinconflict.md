---
title: "IMAPIFormMgrIsInConflict"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormMgrIsInConflict
api_type:
- COM
ms.assetid: 5ca86ee8-1bf6-4ec8-95b3-575c22fbb170
---

# IMAPIFormMgr::IsInConflict

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines whether a form can handle its own message conflicts. A message is in conflict if it has been simultaneously edited by more than one user. This can happen to messages in public folders.
  
```cpp
HRESULT IsInConflict(
  ULONG ulMessageFlags,
  ULONG ulMessageStatus,
  LPCSTR szMessageClass LPMAPIFOLDER pFolderFocus
);
```

## Parameters

 _ulMessageFlags_
  
> [in] A pointer to a bitmask of flags copied from the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property of a message that indicates the current state of the message.
    
 _ulMessageStatus_
  
> [in] A bitmask of client-defined or provider-defined flags copied from the **PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) property of a message that provides additional information about the state of the message.
    
 _szMessageClass_
  
> [in] A string that names the message's message class.
    
 _pFolderFocus_
  
> [in] A pointer to the folder that contains the message. The  _pFolderFocus_ parameter can be NULL if such a folder does not exist (for example, if the message is embedded in another message). 
    
## Return value

S_OK 
  
> The form does not handle its own message conflicts.
    
S_FALSE 
  
> The form handles its own message conflicts, or the message for which information was passed is not in conflict.
    
## Remarks

Form viewers call the **IMAPIFormMgr::IsInConflict** method to discover whether a particular form does not handle its own message conflicts. **IsInConflict** checks the bitmasks in the _ulMessageFlags_ and  _ulMessageStatus_ parameters for the presence of a conflict flag. If a conflict flag is set, **IsInConflict** resolves the message class passed in the _szMessageClass_ parameter and returns S_OK if the form does not handle its own conflicts. **IsInConflict** returns S_FALSE if the form handles its own conflicts. 
  
A form that does not handle its own conflicts must be opened by using the [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md) method and cannot reuse an existing form object. 
  
## Notes to callers

Client applications typically have to deal with conflicts when the applications move from one message to the next or previous message in a folder. If a message is in conflict, but the form server for that message can handle conflicts, the client application should execute its usual code for displaying the next or previous message. If the form server cannot handle conflicts, the client application should continue as if it was unaware of the message class of the next or previous message. 
  
## See also



[IMAPIFormAdviseSink::OnActivateNext](imapiformadvisesink-onactivatenext.md)
  
[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)
  
[PidTagMessageStatus Canonical Property](pidtagmessagestatus-canonical-property.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

