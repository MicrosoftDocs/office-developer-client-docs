---
title: "NOTIFKEY"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.NOTIFKEY
api_type:
- COM
ms.assetid: 031b7e18-59b2-445c-a747-348fda92f458
description: "Last modified: March 09, 2015"
---

# NOTIFKEY

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Uniquely identifies a connection between an advise sink, an advise source, and MAPI.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
   
```cpp
typedef struct
{
  ULONG cb;
  BYTE ab[MAPI_DIM];
} NOTIFKEY, FAR *LPNOTIFKEY;

```

## Members

 **cb**
  
> Count of bytes in the **ab** member. 
    
 **ab**
  
> Array of bytes describing the notification key.
    
## Remarks

The [Subscribe](imapisupport-subscribe.md) and [Notify](imapisupport-notify.md) methods of [IMAPISupport](imapisupportiunknown.md) use the **NOTIFKEY** structure to generate notifications to the appropriate advise sink about the appropriate advise source. 
  
Service providers generate notification keys when their **Advise** method is called and they want to call **Subscribe** to handle the notification registration and the subsequent sending of notifications. A notification key can be the entry identifier of the advise source or it can be any other identifying item such as a constant. For example, a message store provider might use the path of a folder as its notification key. 
  
The notification key should work across multiple processes. 
  
The scope requirements for a notification key resemble those for a long-term entry identifier. However, unlike an entry identifier, a notification key must be binary-comparable. Typically, a notification key includes a **GUID** value defined by the service provider followed by other provider-specific information unique to the object. 
  
For a discussion of the use of the **NOTIFKEY** structure to manage the connections between the advise sinks and the objects that generate the notifications, see [Supporting Event Notification](supporting-event-notification.md). 
  
## See also



[MAPI Structures](mapi-structures.md)

