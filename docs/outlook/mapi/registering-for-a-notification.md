---
title: "Registering for a Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 45625387-dbd2-4ca8-926b-ef87998d01d7
description: "Last modified: July 23, 2011"
 
 
---

# Registering for a Notification

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A client can register for address book or message store notifications as part of its initialization process.
  
MAPI supports notification on the address book regardless of whether any of the address book providers support it. Support for notification on message stores depends on the particular message store provider. To determine whether a particular message store provider supports notifications, check its **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property. If the message store supports notifications, the STORE_NOTIFY_OK bit will be set. 
  
Register for notifications by calling an advise source object's **Advise** method. Many objects implement **Advise** and clients can register with those objects in a variety of ways. 
  
 **To register for a notification**
  
1. Create a MAPI advise sink object and increment its reference count.
    
2. If appropriate, call [HrThisThreadAdviseSink](hrthisthreadadvisesink.md) to create an advise sink object that wraps your original advise sink, then release the original advice sink.. 
    
3. Call one of the following **Advise** methods to complete the registration: 
    
  - Call [IMAPISession::Advise](imapisession-advise.md) to register for session notifications or for notifications on an address book or message store object. 
    
  - Call [IAddrBook::Advise](iaddrbook-advise.md) to register for address book notifications or for notifications on a messaging user, container, or distribution list. 
    
  - Call [IABLogon::Advise](iablogon-advise.md) to register directly with an address book provider for notifications on a messaging user, container, or distribution list. 
    
  - Call [IMsgStore::Advise](imsgstore-advise.md) to register for message store notifications or for notifications on a folder or message. 
    
  - Call [IMSLogon::Advise](imslogon-advise.md) to register directly with a message store provider for notifications on a folder or message. 
    
  - Call [IMAPITable::Advise](imapitable-advise.md) to register for table notifications. 
    
4. Cache the connection number returned from **Advise**.
    
5. If using a wrapped advise sink, release it. Once the wrapped advise sink is registered, you no longer need it.
    
Calling ** IMAPISession::Advise ** enables you to register for critical error notifications on the overall session or for various notifications on individual objects. Sessions send critical error notifications to clients logged on to shared sessions when another client using the shared session calls the [IMAPISession::Logoff](imapisession-logoff.md) method. To register for session notifications, pass NULL for the entry identifier parameter. To register for notifications on an individual object, pass the object's entry identifier. The **IMAPISession** method forwards the call to the appropriate service provider, as determined by the **MAPIUID** portion of the entry identifier. Calling **IMAPISession::Advise** to register for object notifications is simpler than calling a service provider's **Advise** method. 
  
Registering with the address book is similar to registering with the session. To register for critical error notification from the address book, pass NULL for the entry identifier. To register for notifications on a particular address book object, specify the appropriate entry identifier and event or events of interest. Be aware that many address book providers do not support notifications on individual objects. Rather, they support table notifications on their contents and hierarchy tables. 
  
It is good practice to release the advise sink that you implement or create with [HrAllocAdviseSink](hrallocadvisesink.md) immediately after a successful return from an **Advise** call. This is because it is possible for service providers to release your advise sink after the **Advise** call, but before an **Unadvise** call is made. Once you have given the advise source a pointer to your advise sink and the reference count has been incremented on this advise sink, it is wise to release it unless you have a long term use for it. 
  
> [!NOTE]
> All connection numbers that represent valid advisory registrations will not be released until the **Unadvise** call is made. 
  

