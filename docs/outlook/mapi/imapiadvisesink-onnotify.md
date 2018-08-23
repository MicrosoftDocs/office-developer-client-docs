---
title: "IMAPIAdviseSinkOnNotify"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIAdviseSink.OnNotify
api_type:
- COM
ms.assetid: 9eec90d3-2369-4340-86ed-0efa58918ed5
description: "Last modified: March 09, 2015"
---

# IMAPIAdviseSink::OnNotify

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Responds to a notification by performing one or more tasks. The tasks performed depend on the type of event and the object that generates the notification. 
  
```cpp
ULONG OnNotify(
  ULONG cNotif,
  LPNOTIFICATION lpNotifications
);
```

## Parameters

 _cNotif_
  
> [in] The count of [NOTIFICATION](notification.md) structures pointed to by the  _lpNotifications_ parameter. 
    
 _lpNotifications_
  
> [in] A pointer to one or more **NOTIFICATION** structures that provide information about the events that have occurred. 
    
## Return value

S_OK 
  
> The notification was processed successfully.
    
## Remarks

The notification process starts when a client or MAPI makes a call to a service provider's **Advise** method to register to receive a notification of a particular type for a particular object. One of the parameters to the **Advise** method is a pointer to an advise sink object that implements the [IMAPIAdviseSink](imapiadvisesinkiunknown.md) interface. When an event occurs to the target object that corresponds to the registered notification, the service provider, either directly or indirectly through MAPI, calls the advise sink's **OnNotify** method. 
  
The call to **OnNotify** can occur either during the MAPI call that is causing the event or at some later time. On systems that support multiple threads of execution, **OnNotify** can be called either on the same thread that was used for registration or on a different thread. Clients can make sure that the **OnNotify** call is made on the same thread used to call **Advise** by creating the advise sink that they pass to **Advise** with the [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) function. 
  
The  _lpNotifications_ parameter points to one or more **NOTIFICATION** structures that describe what has changed during the event. There is a different type of **NOTIFICATION** structure for each type of event. 
  
The following table lists the values that are used to represent the possible types of events and the structures associated with each value:
  
|**Notification event type**|**Corresponding structure**|
|:-----|:-----|
|**fnevCriticalError** <br/> |[ERROR_NOTIFICATION](error_notification.md) <br/> |
|**fnevNewMail** <br/> |[NEWMAIL_NOTIFICATION](newmail_notification.md) <br/> |
|**fnevObjectCreated** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectDeleted** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectModified** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevObjectCopied** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevSearchComplete** <br/> |[OBJECT_NOTIFICATION](object_notification.md) <br/> |
|**fnevTableModified** <br/> |[TABLE_NOTIFICATION](table_notification.md) <br/> |
|**fnevStatusObjectModified** <br/> |[STATUS_OBJECT_NOTIFICATION](status_object_notification.md) <br/> |
|**fnevExtended** <br/> |[EXTENDED_NOTIFICATION](extended_notification.md) <br/> |
   
For more information about how to set up and stop notifications, see the reference entries for the **Advise** and **Unadvise** methods for any of the following interfaces: [IABLogon](iablogoniunknown.md), [IAddrBook](iaddrbookimapiprop.md), [IMAPIForm](imapiformiunknown.md), [IMAPISession](imapisessioniunknown.md), [IMAPITable](imapitableiunknown.md), [IMsgStore](imsgstoreimapiprop.md), and [IMSLogon](imslogoniunknown.md). 
  
For general information about the notification process, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
## Notes to implementers

Your **OnNotify** implementation will typically consist of one or more blocks of code for each type of notification you expect to receive. Within these blocks of code, perform any tasks that you consider necessary as a response to the notification. For example, suppose you register to receive **fnevObjectModified** notifications on a folder that is included in a dialog box display. In the block of code that you include in your **OnNotify** method to handle **fnevObjectModified** notifications, you might send a Windows message to the dialog box to request an updated display. 
  
Do not modify or free the **NOTIFICATION** structure passed to **OnNotify**. The data in the structure is valid only until **OnNotify** returns. 
  
## Notes to callers

When changes occur to multiple objects, you can notify a registered advise sink in a single call to **OnNotify** or in multiple calls depending on memory constraints. This is true regardless of whether the changes are the result of one method call or several. For example, a call to [IMAPIFolder::CopyMessages](imapifolder-copymessages.md) can affect multiple messages and folders. As a message store provider, you can make one call to **OnNotify** with an **fnevObjectModified** event type for the target folder or many calls, one for each affect messages. Similarly, if a client makes repeated calls to [IMAPIFolder::CreateMessage](imapifolder-createmessage.md), these calls can be combined into one **fnevObjectModified** event for the folder or separated into individual **fnevObjectCreated** events for each new message. 
  
For more information about how and when to generate notifications, see [Event Notification in MAPI](event-notification-in-mapi.md) and [Supporting Event Notification](supporting-event-notification.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|AdviseSink.h and AdviseSink.cpp  <br/> |CAdviseSink::OnNotifyDesc  <br/> |The CAdviseSink class is implemented to handle all notifications in MFCMAPI.  <br/> |
   
## See also



[HrAllocAdviseSink](hrallocadvisesink.md)
  
[HrThisThreadAdviseSink](hrthisthreadadvisesink.md)
  
[IMAPISupport::Notify](imapisupport-notify.md)
  
[NOTIFICATION](notification.md)
  
[IMAPIAdviseSink : IUnknown](imapiadvisesinkiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

