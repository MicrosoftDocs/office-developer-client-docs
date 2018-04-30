---
title: "Threading in MAPI"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 259297d2-acd7-4bc5-9a77-0df92cbfa33e
description: "Last modified: March 09, 2015"
---

# Threading in MAPI

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
A thread is the basic entity to which an operating system allocates CPU time. A thread has its own registers, stack, priority, and storage, but shares an address space and process resources such as access tokens. Threads also share memory, with one thread reading what another thread has written.
  
MAPI clients use the following generic threading models.
  
|**Threading model**|**Description**|
|:-----|:-----|
|Single threading model  <br/> |All objects are used on the single thread.  <br/> |
|Apartment threading model  <br/> |An object can be used only on the thread that created it.  <br/> |
|Free threading, or thread-party, model  <br/> |An object can be used on any thread.  <br/> |
   
MAPI uses the free threading model, supporting thread-safe objects that can be used on any thread at any time. OLE uses the apartment threading model. The apartment threading model supports objects that must be explicitly transferred when a thread other than the one that created the object needs to use that object.
  
The mechanism that OLE uses to transfer objects from one thread to another is known as marshaling. Marshaling involves a stub object and a proxy object. These special objects package the parameters of the interface in the object to be marshaled, transfer these parameters to the other thread, and unpackage them upon arrival. Conflict between the two multithreaded models arises when a free-threading MAPI object is sent to another process using OLE "lightweight" Remote Procedure Call, or LRPC. LRPC changes the object's semantics from free threading to apartment threading by interposing stub and proxy interfaces with apartment threading behavior between the object and its caller. Awareness of the situations in MAPI that lead to this conflict can help clients and service providers prevent problems from occurring.
  
A MAPI object can be accessed:
  
- Through direct calls to its methods using an interface pointer returned by a service provider or MAPI linked to the client's process, such as the session object returned from [MAPILogonEx](mapilogonex.md).
    
- Through indirect calls to its methods using an interface pointer returned by any service provider, such as the folder object copied from another folder in [IMAPIFolder::CopyFolder](imapifolder-copyfolder.md).
    
- Through a callback function, such as the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method passed to a service provider or to MAPI in an **Advise** call or the methods that can show progress on a lengthy operation. 
    

