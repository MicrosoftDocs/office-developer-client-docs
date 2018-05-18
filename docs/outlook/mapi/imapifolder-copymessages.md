---
title: "IMAPIFolderCopyMessages"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.CopyMessages
api_type:
- COM
ms.assetid: 4c7d2110-3fcb-4b9f-bf20-1dc1a611161d
description: "Last modified: March 09, 2015"
---

# IMAPIFolder::CopyMessages

  
  
**Applies to**: Outlook 
  
Copies or moves one or more messages.
  
```cpp
HRESULT CopyMessages(
  LPENTRYLIST lpMsgList,
  LPCIID lpInterface,
  LPVOID lpDestFolder,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _lpMsgList_
  
> [in] A pointer to an array of [ENTRYLIST](entrylist.md) structures that identify the message or messages to copy or move. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the destination folder pointed to by the  _lpDestFolder_ parameter. Passing NULL results in the service provider returning the standard folder interface, [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md). Clients must pass NULL. Other callers can set the  _lpInterface_ parameter to IID_IUnknown, IID_IMAPIProp, IID_IMAPIContainer, or IID_IMAPIFolder. 
    
 _lpDestFolder_
  
> [in] A pointer to the open folder to receive the copied or moved messages.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays. The  _ulUIParam_ parameter is ignored unless the client sets the MESSAGE_DIALOG flag in the  _ulFlags_ parameter and passes NULL in the  _lpProgress_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator. If NULL is passed in  _lpProgress_, the message store provider displays a progress indicator by using the MAPI progress object implementation. The  _lpProgress_ parameter is ignored unless the MESSAGE_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the copy or move operation is accomplished. The following flags can be set:
    
MAPI_DECLINE_OK 
  
> Informs the message store provider to immediately return MAPI_E_DECLINE_COPY if it implements **IMAPIFolder::CopyMessages** by calling the support object's [IMAPISupport::DoCopyTo](imapisupport-docopyto.md) or [IMAPISupport::DoCopyProps](imapisupport-docopyprops.md) method. 
    
MESSAGE_DIALOG 
  
> Displays a progress indicator as the operation proceeds.
    
MESSAGE_MOVE 
  
> The message or messages are to be moved instead of copied. If MESSAGE_MOVE is not set, the messages are copied.
    
## Return value

S_OK 
  
> The message or messages have been successfully copied or moved.
    
MAPI_E_DECLINE_COPY 
  
> The provider implements this method by calling a support object method, and the caller has passed the MAPI_DECLINE_OK flag.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but not all entries were successfully copied or moved. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPIFolder::CopyMessages** method copies or moves messages to another folder. 
  
Messages that are opened with read/write permission can be moved or copied. 
  
## Notes to implementers

If you are copying messages to another message store without using the [IMAPISupport::CopyMessages](imapisupport-copymessages.md) method, you must first call [IMAPIFolder::SetReadFlags](imapifolder-setreadflags.md) with the GENERATE_RECEIPT_ONLY flag set. The receiving message store is not responsible for generating read reports for the copied or moved messages. If you are calling **IMAPISupport::CopyMessages** to implement **IMAPIFolder::CopyMessages**, do not call **SetReadFlags**; MAPI will call it. 
  
Your implementation can move or copy the messages in any order and generate read status reports in any order. That is, you can finish copying messages before generating any of the read status reports or send the reports before your implementation starts the copy operation. However, read reports should be sent for all messages to be copied, regardless of whether the copy is successful.
  
When the copy or move operation involves more than one message, perform the operation as completely as possible. Do not stop the operation prematurely unless a failure occurs that is beyond your control, such as running out of memory, running out of disk space, or corruption in the message store.
  
Try to maintain entry identifiers across move or copy operations. You should also preserve entry identifiers, although it is not required.
  
Send notifications when you move or copy messages so that clients are forewarned that their calls to the messages' [IMAPIProp::SaveChanges](imapiprop-savechanges.md) methods may fail. 
  
Do not include a message's status in the copy or move operation. Moving or copying a message status greatly affects performance.
  
## Notes to callers

Use **IMAPIFolder::CopyMessages** to populate search-results folders, where messages are often grouped by parent folder. 
  
Expect these return values under the following conditions.
  
|**Condition**|**Return value**|
|:-----|:-----|
|**IMAPIFolder::CopyMessages** has successfully copied or moved every message.  <br/> |S_OK  <br/> |
|**IMAPIFolder::CopyMessages** was unable to successfully copy or move every message.  <br/> |MAPI_W_PARTIAL_COMPLETION  <br/> |
|**IMAPIFolder::CopyMessages** was unable to complete.  <br/> |Any error value  <br/> |
   
When **IMAPIFolder::CopyMessages** is unable to complete, do not assume that no work was done. **IMAPIFolder::CopyMessages** might have been able to copy or move one or more messages before encountering the error. 
  
## See also



[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)

