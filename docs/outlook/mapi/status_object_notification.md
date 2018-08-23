---
title: "STATUS_OBJECT_NOTIFICATION"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.STATUS_OBJECT_NOTIFICATION
api_type:
- COM
ms.assetid: 2872130d-a36b-46ea-bfd1-4700fe3dd41b
description: "Last modified: March 09, 2015"
---

# STATUS_OBJECT_NOTIFICATION

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a status object that has been affected by a change. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct
{
  ULONG cbEntryID;
  LPENTRYID lpEntryID;
  ULONG cValues;
  LPSPropValue lpPropVals;
} STATUS_OBJECT_NOTIFICATION;

```

## Members

 **cbEntryID**
  
> Count of bytes in the entry identifier pointed to by the **lpEntryID** member. 
    
 **lpEntryID**
  
> Pointer to the entry identifier of the changed status object.
    
 **cValues**
  
> Count of [SPropValue](spropvalue.md) structures in the array pointed to by the **lpPropVals** member. 
    
 **lpPropVals**
  
> Pointer to an array of **SPropValue** structures that describe the properties of the changed status object. 
    
## Remarks

The **STATUS_OBJECT_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. The **STATUS_OBJECT_NOTIFICATION** structure is included with a status object notification for an event of type  _fnevStatusObjectModified_. Status object notification is an internal MAPI notification; clients and service providers cannot register for it and service providers cannot generate it.
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the **IMAPISupport** method to generate notifications.  <br/> |
   
## See also



[NOTIFICATION](notification.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

