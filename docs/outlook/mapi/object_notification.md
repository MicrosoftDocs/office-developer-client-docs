---
title: "OBJECT_NOTIFICATION"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.OBJECT_NOTIFICATION
api_type:
- COM
ms.assetid: de3a2297-e0cc-427b-a978-52bade4d9bce
description: "Last modified: March 09, 2015"
---

# OBJECT_NOTIFICATION

  
  
**Applies to**: Outlook 
  
Contains information about an object that has undergone a change, such as being copied or modified.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _OBJECT_NOTIFICATION
{
  ULONG cbEntryID;
  LPENTRYID lpEntryID;
  ULONG ulObjType;
  ULONG cbParentID;
  LPENTRYID lpParentID;
  ULONG cbOldID;
  LPENTRYID lpOldID;
  ULONG cbOldParentID;
  LPENTRYID lpOldParentID;
  LPSPropTagArray lpPropTagArray;
} OBJECT_NOTIFICATION;

```

## Members

 **cbEntryID**
  
> Count of bytes in the entry identifier pointed to by the **lpEntryID** member. 
    
 **lpEntryID**
  
> Pointer to the entry identifier of the affected object.
    
 **ulObjType**
  
> Type of object affected. Possible types are as follows:
    
MAPI_STORE 
  
> Message store. 
    
MAPI_ADDRBOOK 
  
> Address book. 
    
MAPI_FOLDER 
  
> Folder.
    
MAPI_ABCONT 
  
> Address book container.
    
MAPI_MESSAGE 
  
> Message.
    
MAPI_MAILUSER 
  
> Messaging user.
    
MAPI_ATTACH 
  
> Attachment.
    
MAPI_DISTLIST 
  
> Distribution list.
    
MAPI_PROFSECT 
  
> Profile section.
    
MAPI_STATUS 
  
> Status object.
    
MAPI_SESSION 
  
> Session object.
    
 **cbParentID**
  
> Count of bytes in the entry identifier pointed to by the **lpParentID** member. 
    
 **lpParentID**
  
> Pointer to the entry identifier of the parent of the affected object.
    
 **cbOldID**
  
> Count of bytes in the entry identifier pointed to by the **lpOldID** member. 
    
 **lpOldID**
  
> Pointer to the entry identifier of the original object. This pointer can be NULL if the event does not require an original object.
    
 **cbOldParentID**
  
> Count of bytes in the entry identifier pointed to by the **lpOldParentID** member. 
    
 **lpOldParentID**
  
> Pointer to the entry identifier of the parent of the original object. This pointer can be NULL if the event does not require an original object.
    
 **lpPropTagArray**
  
> Pointer to an [SPropTagArray](sproptagarray.md) structure that contains the property tags identifying properties affected by the event. 
    
## Remarks

The **OBJECT_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. When the **info** member of a **NOTIFICATION** structure contains an **OBJECT_NOTIFICATION** structure, the **ulEventType** member of the **NOTIFICATION** structure is set to one of the following types of events: 
  
- fnevObjectCreated
    
- fnevObjectModified
    
- fnevObjectDeleted
    
- fnevObjectMoved
    
- fnevObjectCopied
    
- fnevSearchComplete
    
The search complete event, represented by the fnevSearchComplete event type, indicates that the initial search of the domain for one search folder has completed.
  
The following members that contain information about the original object are used only in move and copy events. 
  
- **cbOldID**
    
- **lpOldID**
    
- **cbOldParentID**
    
- **lpOldParentID**
    
These members do not apply to the other types of events.
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the [IMAPISupport](imapisupportiunknown.md) method to generate notifications.  <br/> |
   
## See also



[NOTIFICATION](notification.md)
  
[SPropTagArray](sproptagarray.md)


[MAPI Structures](mapi-structures.md)

