---
title: "NOTIFICATION"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.NOTIFICATION
api_type:
- COM
ms.assetid: 01b6e695-a649-4efd-a893-7586b476467e
description: "Last modified: March 09, 2015"
---

# NOTIFICATION

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains information about an event that has occurred and the data that has been affected by the event.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct
{
  ULONG ulEventType;
  union
  {
    ERROR_NOTIFICATION err;
    NEWMAIL_NOTIFICATION newmail;
    OBJECT_NOTIFICATION obj;
    TABLE_NOTIFICATION tab;
    EXTENDED_NOTIFICATION ext;
    STATUS_OBJECT_NOTIFICATION statobj;
  } info;
} NOTIFICATION, FAR *LPNOTIFICATION;

```

## Members

 **ulEventType**
  
> Type of notification event that occurred. The value of the **ulEventType** member corresponds to the structure that is included in the **info** union. The **ulEventType** member can be set to one of the following values: 
    
 _fnevCriticalError_
  
> A global error has occurred, such as a session shut down in progress. The **info** member contains an [ERROR_NOTIFICATION](error_notification.md) structure. 
    
 _fnevExtended_
  
> An internal event defined by a particular service provider has occurred. The **info** member contains an [EXTENDED_NOTIFICATION](extended_notification.md) structure. 
    
 _fnevNewMail_
  
> A message has been delivered to the appropriate receive folder for the message class and is waiting to be processed. The **info** member contains an [NEWMAIL_NOTIFICATION](newmail_notification.md) structure. 
    
 _fnevObjectCopied_
  
> A MAPI object has been copied. The **info** member contains an [OBJECT_NOTIFICATION](object_notification.md) structure. 
    
 _fnevObjectCreated_
  
> A MAPI object has been created. The **info** member contains an **OBJECT_NOTIFICATION** structure. 
    
 _fnevObjectDeleted_
  
> A MAPI object has been deleted. The **info** member contains an **OBJECT_NOTIFICATION** structure. 
    
 _fnevObjectModified_
  
> A MAPI object has changed. The **info** member contains an **OBJECT_NOTIFICATION** structure. 
    
 _fnevObjectMoved_
  
> A message store or address book object has been moved. The **info** member contains an **OBJECT_NOTIFICATION** structure. 
    
 _fnevSearchComplete_
  
> A search operation has finished and the results are available. The **info** member contains an **OBJECT_NOTIFICATION** structure. 
    
 _fnevTableModified_
  
> Information in a table has changed. The **info** member contains an [TABLE_NOTIFICATION](table_notification.md) structure. 
    
 **info**
  
> Union of notification structures describing the affected data for a particular type of event. The structure included in the **info** member depends on the value of the **ulEventType** member. 
    
## Remarks

One or more **NOTIFICATION** structures are passed as input parameters with every call to a registered advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method. The **NOTIFICATION** structures contain information about the particular events that have occurred and describe the affected objects. 
  
Before clients or service providers receiving a notification can use the structure to process the event, they must check the event type as indicated in the **ulEventType** member. For example, the code sample that is shown here checks for the arrival of a new message and upon detecting an event of this kind, prints out the message class of the message. 
  
```
if (pNotif -> ulEventType == fnevNewMail)
{
printf("%s\n", pNotif -> newmail.lpszMessageClass)
}

```

For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the [IMAPISupport](imapisupportiunknown.md) method to generate notifications.  <br/> |
   
## See also

#### Reference

[ERROR_NOTIFICATION](error_notification.md)
  
[EXTENDED_NOTIFICATION](extended_notification.md)
  
[NEWMAIL_NOTIFICATION](newmail_notification.md)
  
[OBJECT_NOTIFICATION](object_notification.md)
  
[STATUS_OBJECT_NOTIFICATION](status_object_notification.md)
  
[TABLE_NOTIFICATION](table_notification.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

