---
title: "HrThisThreadAdviseSink"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HrThisThreadAdviseSink
api_type:
- COM
ms.assetid: 12c07302-472f-4e4f-8087-1bdf0dc09a5a
description: "Last modified: March 09, 2015"
---

# HrThisThreadAdviseSink

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates an advise sink that wraps an existing advise sink for thread safety. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
HrThisThreadAdviseSink(
  LPMAPIADVISESINK lpAdviseSink,
  LPMAPIADVISESINK FAR * lppAdviseSink
);
```

## Parameters

 _lpAdviseSink_
  
> [in] Pointer to the advise sink to be wrapped. 
    
 _lppAdviseSink_
  
> [out] Pointer to a pointer to a new advise sink that wraps the advise sink pointed to by the  _lpAdviseSink_ parameter. 
    
## Return value

None.
  
## Remarks

The purpose of the wrapper is to make sure that notification is called on the same thread that called the **HrThisThreadAdviseSink** function. This function is used to protect notification callbacks that must run on a particular thread. 
  
Client applications should use **HrThisThreadAdviseSink** to restrict when notifications are generated, that is, when calls are made to the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method of the advise sink object passed by the client in a previous **Advise** call. If notifications are allowed to be generated arbitrarily, a notification implementation might force a client into multithreaded operation when that would not be appropriate. For example, a client might use a library, such as one of the Microsoft Foundation Class Libraries, that does not support multithreaded calls. Notification on a different thread would make such a client difficult to test and prone to error. 
  
 **HrThisThreadAdviseSink** makes sure that **OnNotify** calls occur only at these appropriate times: 
  
- During processing of a call to any MAPI method. 
    
- During processing of Windows messages. 
    
When **HrThisThreadAdviseSink** is implemented, any calls to the new advise sink's **OnNotify** method on any thread cause the original notification method to be executed on the thread on which **HrThisThreadAdviseSink** was called. 
  
For more information about notification and advise sinks, see [Event Notification in MAPI](event-notification-in-mapi.md) and [Implementing an Advise Sink Object](implementing-an-advise-sink-object.md). 
  

