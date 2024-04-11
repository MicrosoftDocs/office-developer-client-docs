---
title: "Implementing Thread-Safe Objects"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 3c911694-b953-4d35-9a3a-22c17cfd79bc
 
 
---

# Implementing Thread-Safe Objects

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
With objects that are returned from interface method calls directly, it is the provider's responsibility to ensure thread-safety. With callback objects, it is the client application's responsibility.
  
A client can implement a thread-safe notification callback by calling the MAPI utility [HrThisThreadAdviseSink](hrthisthreadadvisesink.md). **HrThisThreadAdviseSink** transforms a non-thread-safe advise sink into a thread-safe one. For progress callbacks, there is no such utility. A client can choose to use the MAPI thread-safe progress object or create one manually. 
  
A thread-safe object might or might not also be thread-aware. A thread-aware object maintains a separate context for every thread that is using it. Service providers are not required to support thread-awareness in their thread-safe objects, although supporting thread-awareness can be useful in some situations. Two MAPI tables always provide their own context by definition. One table used on different threads does not and should not provide unique context.
  
A client can choose between receiving notifications on the same thread that was used for the **MAPIInitialize** call, on the same thread that was used for the **Advise** call, or on a separate thread owned by MAPI. To ensure that notifications arrive on the same thread that was used to call **MAPIInitialize**, a client calls [MAPIInitialize](mapiinitialize.md) and passes zero in the **ulFlags** member of the [MAPIINIT_0](mapiinit_0.md) structure. Notifications are then delivered during the main message loop. 
  
To receive notifications on the MAPI-owned thread, a client calls **MAPIInitialize** with the **ulFlags** member of the **MAPIINIT_0** structure set to MAPI_MULTITHREAD_NOTIFICATIONS. The **Advise** call is made with the client's advise sink object rather than a wrapped version. 
  
To ensure that notifications arrive on the same thread that was used to call **Advise**, a client calls [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) and passes the newly created wrapped advise sink to **Advise** rather than the original advise sink. **MAPIInitialize** can be called with either flag value. 
  

