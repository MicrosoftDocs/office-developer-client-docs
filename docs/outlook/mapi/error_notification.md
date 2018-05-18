---
title: "ERROR_NOTIFICATION"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ERROR_NOTIFICATION
api_type:
- COM
ms.assetid: 6c5bb383-f8e2-4d79-bcf2-aa86c130e8b1
description: "Last modified: March 09, 2015"
---

# ERROR_NOTIFICATION

  
  
**Applies to**: Outlook 
  
Describes information that relate to a critical error. This causes an error notification to be generated. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _ERROR_NOTIFICATION
{
  ULONG cbEntryID;
  LPENTRYID lpEntryID;
  SCODE scode;
  ULONG ulFlags;
  LPMAPIERROR lpMAPIError;
} ERROR_NOTIFICATION;
```

## Members

 **cbEntryID**
  
> Count of bytes in the entry identifier pointed to by **lpEntryID**. 
    
 **lpEntryID**
  
> Pointer to the entry identifier of the object that causes the error.
    
 **scode**
  
> Error value for the critical error. 
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the text pointed to by the **lpszError** member in the structure pointed to by **lpMAPIError**. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 **lpMAPIError**
  
> Pointer to a [MAPIERROR](mapierror.md) structure describing the error. 
    
## Remarks

The **ERROR_NOTIFICATION** structure is one of the members of the union of structures included in the **info** member of the [NOTIFICATION](notification.md) structure. When the **info** member of a **NOTIFICATION** structure contains an **ERROR_NOTIFICATION** structure, the **ulEventType** member of the **NOTIFICATION** structure is set to  _fnevCriticalError_.
  
The value of the **cbEntryID** member and the **lpEntryID** member can be NULL. 
  
For more information about notification, see the topics described in the following table.
  
|**Topic**|**Description**|
|:-----|:-----|
|[Event Notification in MAPI](event-notification-in-mapi.md) <br/> |General overview of notification and notification events.  <br/> |
|[Handling Notifications](handling-notifications.md) <br/> |Discussion of how clients should handle notifications.  <br/> |
|[Supporting Event Notification](supporting-event-notification.md) <br/> |Discussion of how service providers can use the **IMAPISupport** method to generate notifications.  <br/> |
   
## See also



[MAPIERROR](mapierror.md)
  
[NOTIFICATION](notification.md)


[MAPI Structures](mapi-structures.md)

