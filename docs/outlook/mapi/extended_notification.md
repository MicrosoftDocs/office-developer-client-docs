---
title: "EXTENDED_NOTIFICATION"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.EXTENDED_NOTIFICATION
api_type:
- COM
ms.assetid: f01fce7b-a038-4002-8bad-0e6a51ae9d05
description: "Last modified: March 09, 2015"
---

# EXTENDED_NOTIFICATION

  
  
**Applies to**: Outlook 
  
Describes information that relates to an event that is service provider-specific. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _EXTENDED_NOTIFICATION
{
  ULONG ulEvent;
  ULONG cb;
  LPBYTE pbEventParameters;
} EXTENDED_NOTIFICATION;

```

## Members

 **ulEvent**
  
> Extended event code that is defined by the provider.
    
 **cb**
  
> Count of bytes in the event-specific parameters pointed to by **pbEventParameters**. 
    
 **pbEventParameters**
  
> Pointer to event-specific parameters. The type of parameters that are used depends on the value of the **ulEvent** member; these parameters are documented by the provider that issued the event. 
    
## Remarks

The **EXTENDED_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. When the **info** member of a **NOTIFICATION** structure contains an **EXTENDED_NOTIFICATION** structure, the **ulEventType** member of the **NOTIFICATION** structure is set to  _fnevExtended_.
  
The extended event is defined by a service provider to represent a type of change that cannot be covered by any of the other predefined events. Only clients that know before they register that a service provider supports an extended event can register for that event. It is not possible for clients to determine without advanced knowledge if a service provider supports an extended event. If a service provider supports an extended event, it shows how to handle such an event when it is received.
  
An extended notification is sent by the session when a client logs off. Register for this notification by calling [IMAPISession::Advise](imapisession-advise.md) with the  _lpEntryID_ parameter set to NULL and the  _cbEntryID_ parameter set to zero. 
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the [IMAPISupport](imapisupportiunknown.md) methods to generate notifications.  <br/> |
   
## See also

#### Reference

[NOTIFICATION](notification.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

