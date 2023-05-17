---
title: "NEWMAIL_NOTIFICATION"
description: "Provides the property info, members, and remarks for NEWMAIL_NOTIFICATION, which describes information that relates to the arrival of a new message."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.NEWMAIL_NOTIFICATION
api_type:
- COM
ms.assetid: 49913050-900a-4b05-84c4-c596a93ce68b
---

# NEWMAIL_NOTIFICATION

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes information that relates to the arrival of a new message. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _NEWMAIL_NOTIFICATION
{
  ULONG cbEntryID;
  LPENTRYID lpEntryID;
  ULONG cbParentID;
  LPENTRYID lpParentID;
  ULONG ulFlags;
  LPSTR lpszMessageClass;
  ULONG ulMessageFlags;
} NEWMAIL_NOTIFICATION;

```

## Members

 **cbEntryID**
  
> Count of bytes in the entry identifier pointed to by the **lpEntryID** member. 
    
 **lpEntryID**
  
> Pointer to the entry identifier of the newly arrived message.
    
 **cbParentID**
  
> Count of bytes in the entry identifier pointed to by the **lpParentID** member. 
    
 **lpParentID**
  
> Pointer to the entry identifier of the receive folder for the newly arrived message.
    
 **ulFlags**
  
> Bitmask of flags used to describe the format of the string properties included with the message. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 **lpszMessageClass**
  
> Pointer to the message class of the newly arrived message. 
    
 **ulMessageFlags**
  
> Bitmask of flags that describes the current state of the newly arrived message. The **ulMessageFlags** member is a copy of the message's **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property.
    
## Remarks

The **NEWMAIL_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. When the **info** member of a **NOTIFICATION** structure contains a **NEWMAIL_NOTIFICATION** structure, the **ulEventType** member of the **NOTIFICATION** structure is set to  _fnevNewMail._
  
MAPI uses the **NEWMAIL_NOTIFICATION** structure only as a member of the **NOTIFICATION** structure, which holds information about a notification event for the advise sink. 
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events. |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications. |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the [IMAPISupport](imapisupportiunknown.md) method to generate notifications. |
   
## See also



[NOTIFICATION](notification.md)
  
[PidTagMessageFlags Canonical Property](pidtagmessageflags-canonical-property.md)


[MAPI Structures](mapi-structures.md)

