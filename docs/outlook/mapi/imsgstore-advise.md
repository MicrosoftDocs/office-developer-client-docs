---
title: "IMsgStoreAdvise"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.Advise
api_type:
- COM
ms.assetid: 8c57e743-a798-4e39-a61a-46dff8b1ac7c
description: "Last modified: March 09, 2015"
---

# IMsgStore::Advise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Registers to receive notification of specified events that affect the message store.
  
```cpp
HRESULT Advise(
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulEventMask,
  LPMAPIADVISESINK lpAdviseSink,
  ULONG_PTR lpulConnection
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the folder or message about which notifications should be generated, or **null**. If  _lpEntryID_ is set to NULL, **Advise** registers for notifications on the entire message store. 
    
 _ulEventMask_
  
> [in] A mask of values that indicate the types of notification events that the caller is interested in and should be included in the registration. There is a corresponding [NOTIFICATION](notification.md) structure associated with each type of event that holds information about the event. The following are valid values for the  _ulEventMask_ parameter: 
    
 _fnevCriticalError_
  
> Registers for notifications about severe errors, such as insufficient memory.
    
 _fnevExtended_
  
> Registers for notifications about events specific to the particular message store provider.
    
 _fnevNewMail_
  
> Registers for notifications about the arrival of new messages. 
    
 _fnevObjectCreated_
  
> Registers for notifications about the creation of a new folder or message.
    
 _fnevObjectCopied_
  
> Registers for notifications about a folder or message being copied.
    
 _fnevObjectDeleted_
  
> Registers for notifications about a folder or message being deleted.
    
 _fnevObjectModified_
  
> Registers for notifications about a folder or message being modified.
    
 _fnevObjectMoved_
  
> Registers for notifications about a folder or message being moved.
    
 _fnevSearchComplete_
  
> Registers for notifications about the completion of a search operation.
    
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object to receive the subsequent notifications. This advise sink object must have already been allocated.
    
 _lpulConnection_
  
> [out] A pointer to a nonzero number that represents the connection between the caller's advise sink object and the session. 
    
 _lpAdviseSink_
  
> [in] A pointer to an advise sink object to receive the subsequent notifications. This advise sink object must have already been allocated. 
    
 _lpulConnection_
  
> [out] A pointer to a nonzero connection number that represents the connection between the caller's advise sink object and the message store.
    
## Return value

S_OK 
  
> The registration was successful.
    
MAPI_E_NO_SUPPORT 
  
> The message store provider does not support registration for notification through the message store.
    
## Remarks

The **IMsgStore::Advise** method establishes a connection between the caller's advise sink object and either the message store or an object in the message store. This connection is used to send notifications to the advise sink when one or more events, as specified in the  _ulEventMask_ parameter, occur to the advise source object. When the  _lpEntryID_ parameter points to a valid entry identifier, the advise source is the object identified by this entry identifier. When  _lpEntryID_ is NULL, the advise source is the message store. 
  
To send a notification, either the message store provider or MAPI calls the registered advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method. One of the parameters to **OnNotify**, a notification structure, contains information that describes the specific event.
  
## Notes to implementers

You can support notification with or without help from MAPI. MAPI has three support object methods for helping service providers implement notification: [IMAPISupport::Subscribe](imapisupport-subscribe.md), [IMAPISupport::Unsubscribe](imapisupport-unsubscribe.md), and [IMAPISupport::Notify](imapisupport-notify.md). If you elect to use the MAPI support methods, call **Subscribe** when your **Advise** method is called and release the  _lpAdviseSink_ pointer. 
  
If you elect to support notification yourself, call the [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28v=VS.85%29.aspx) method of the advise sink represented by the  _lpAdviseSink_ parameter to keep a copy of this pointer. Maintain this copy until your [IMsgStore::Unadvise](imsgstore-unadvise.md) method is called to cancel the registration. 
  
Regardless of how you support notification, assign a nonzero connection number to the notification registration and return it in the  _lpulConnection_ parameter. Do not release this connection number until **Unadvise** has been called and has completed. 
  
## Notes to callers

On systems that support multiple threads of execution, the call to **OnNotify** can also occur on any thread at any time. If you must be assured that notifications occur only at a particular time on a particular thread, call the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function to generate the advise sink object that you pass to **Advise**. 
  
After a call to **Advise** has succeeded and before **Unadvise** has been called to cancel the registration, be prepared for the advise sink object to be released. You should release your advise sink object after **Advise** returns unless you have a specific long-term use for it. 
  
For more information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
For more information about handling notifications, see [Handling Notifications](handling-notifications.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|BaseDialog.cpp  <br/> |CBaseDialog::OnNotificationsOn  <br/> |MFCMAPI uses the **IMsgStore::Advise** method to register for notifications on the entire message store.  <br/> |
   
## See also



[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMsgStore::Unadvise](imsgstore-unadvise.md)
  
[NOTIFICATION](notification.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

