---
title: "IMAPISupportCopyMessages"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.CopyMessages
api_type:
- COM
ms.assetid: 70f67614-af0d-43f6-99f6-391a2f5673cb
description: "Last modified: July 23, 2011"
---

# IMAPISupport::CopyMessages

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies or moves messages from one folder to another folder.
  
```cpp
HRESULT CopyMessages(
  LPCIID lpSrcInterface,
  LPVOID lpSrcFolder,
  LPENTRYLIST lpMsgList,
  LPCIID lpDestInterface,
  LPVOID lpDestFolder,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _lpSrcInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the folder that contains the messages to be copied or moved.
    
 _lpSrcFolder_
  
> [in] A pointer to the folder that contains the messages to be copied or moved.
    
 _lpMsgList_
  
> [in] A pointer to an array of entry identifiers that identify the messages to be copied or moved. 
    
 _lpDestInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the destination folder for the copied or moved messages.
    
 _lpDestFolder_
  
> [in] A pointer to the destination folder for the copied or moved messages. This folder must be open.
    
 _ulUIParam_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the MESSAGE_DIALOG flag is set in  _ulFlags_.
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the MESSAGE_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the copy or move operation is accomplished. The following flags can be set:
    
MESSAGE_DIALOG 
  
> Requests the display of a progress indicator.
    
MESSAGE_MOVE 
  
> The messages should be moved, instead of copied. If MESSAGE_MOVE is not set, the messages are copied.
    
## Return value

S_OK 
  
> The copy or move operation was successful.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The **IMAPISupport::CopyMessages** method is implemented for message store provider support objects. Message store providers can call **IMAPISupport::CopyMessages** in their implementation of [IMAPIFolder::CopyMessages](imapifolder-copymessages.md) to copy or move one or more messages from one folder to another. As part of the **IMAPISupport::CopyMessages** call, the message store provider can specify that MAPI should display a progress indicator. 
  
## See also



[IMAPIFolder::CopyMessages](imapifolder-copymessages.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

