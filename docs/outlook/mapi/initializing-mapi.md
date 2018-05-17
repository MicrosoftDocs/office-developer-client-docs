---
title: "Initializing MAPI"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 22ee8157-d74e-4a94-9c76-b9ac736d5211
description: "Last modified: July 23, 2011"
 
 
---

# Initializing MAPI

  
  
**Applies to**: Outlook 
  
All client applications that use the MAPI libraries must call the **MAPIInitialize** function. For more information, see [MAPIInitialize](mapiinitialize.md). **MAPIInitialize** initializes global data for the session and prepares the MAPI libraries to accept calls. There are a few flags that are important to set in some situations: 
  
- MAPI_NT_SERVICE
    
    Set the MAPI_NT_SERVICE flag if your client is implemented as a Windows service. If your client is a Windows service and you do not set this flag, MAPI will not recognize it as a service. 
    
- MAPI_MULTITHREAD_NOTIFICATIONS
    
    The MAPI_MULTITHREAD_NOTIFICATIONS flag relates to how MAPI manages notifications. MAPI creates a hidden window that receives window messages when changes occur to an object generating notifications. The window messages are processed at some point, causing the notifications to be sent and the appropriate [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) methods to be called. 
    
- MAPI_NO_COINIT
    
    Set the MAPI_NO_COINT flag so that **MAPIInitialize** does not try to initialize COM with a call to [CoInitialize](http://msdn.microsoft.com/en-us/library/ms886303.aspx). If a **MAPIINIT_0** structure is passed into **MAPIInitialize** with  _ulFlags_ set to MAPI_NO_COINIT, MAPI will assume that COM has already been initialized and bypass the call to **CoInitialize**.
    
If MAPI_MULTITHREAD_NOTIFICATIONS flag is not passed, MAPI creates the notification window on the thread that was used for your first **MAPIInitialize** call. MAPI creates the notification window on a separate thread if MAPI_MULTITHREAD_NOTIFICATIONS is passed — a thread dedicated to handling notifications. MAPI expects the thread that is used to create the hidden notification window to: 
  
- Have a message loop.
    
- Remain unblocked throughout the life of the session.
    
- Have a longer lifetime than any other thread created by your client. 
    
You can choose which thread is used by setting a flag in the first **MAPIInitialize** call. The danger in allowing one of your threads to handle the notifications is that if the thread disappears, the notification window is destroyed and notifications can no longer be sent to any of your other threads. Also, special processing might be needed to control the dispatching of the notification messages that are posted to the hidden window's message queue. 
  
If you use a separate window to handle notifications, be assured that notifications will appear at the appropriate time on an appropriate thread. You will not need any special code to check for and process the Windows messages that are posted to the notification window. 
  
MAPI recommends that the following types of client applications use a separate thread to create the hidden window for notification support:
  
- All multithreaded clients.
    
- Single-threaded Windows services and Win32 console applications.
    
- Single-threaded clients that do not need to use their main thread for notification.
    
To use the separate thread approach, call **MAPIInitialize** on every thread, setting the MAPI_MULTITHREAD_NOTIFICATIONS flag. 
  
> [!NOTE]
> Only a client's first call to **MAPIInitialize** causes a hidden window to be created to support notifications. Subsequent calls only cause a reference count to be incremented. 
  

