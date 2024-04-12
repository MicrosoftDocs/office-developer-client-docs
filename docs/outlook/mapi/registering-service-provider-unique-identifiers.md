---
title: "Registering Service Provider Unique Identifiers"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 964fceb4-8a1c-46c1-98e1-a325c9259f8b
 
 
---

# Registering Service Provider Unique Identifiers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Address book, message store, and transport providers use a unique identifier known as a [MAPIUID](mapiuid.md) to register to service objects of various types. A **MAPIUID** is a 16-byte identifier that contains a GUID. You can create a **MAPIUID** by using the following procedure: 
  
1. Define a constant.
    
2. Invoke the Visual Studio*Create GUID** tool. 
    
For example, an address book provider might include the following constant in a header file to define a **MAPIUID**:
  
 `#define AB_UID_PROVIDER { 0Xe3, 0x3c, 0x67, 0xa0, \ 0xc8, 0x1f, 0x11, 0xce, \ 0xb2, 0xe4, 0x0, 0xaa, \ 0x0, 0x51, 0xe, 0x3b }`
  
 **To register a MAPIUID if your provider is an address book or message store provider**
  
1. Call [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md).
    
2. Register a **MAPIUID** for each logon object that you instantiate and include this **MAPIUID** in the first 16 bytes of the **ab** member of every entry identifier that you create. MAPI uses **MAPIUID** structures to associate objects with service providers. When a client calls the [IMAPISession::OpenEntry](imapisession-openentry.md) method to open an object, MAPI examines the **MAPIUID** portion of the entry identifier, matching it against the registered **MAPIUID**, to determine which logon object should receive the open request.
    
3. If your provider is a transport, register one or more **MAPIUID** structures when MAPI calls your **IXPLogon::AddressTypes** method. MAPI uses the **MAPIUID** structures registered by transport providers to assign responsibility for message delivery. 
    
Although service providers typically register a single **MAPIUID**, you can register multiple **MAPIUID** structures. If your address book or message store provider supports multiple logon objects, perhaps by permitting a user to add more than one instance of your provider to their profile, you might want to implement a different **MAPIUID** for each logon object. There are a few other reasons to support more than one **MAPIUID**:
  
- You must support more than one version of your provider and the entry identifiers must represent the appropriate version. Assign a different **MAPIUID** for each version. 
    
- You want to distinguish between the types of objects you support. For example, an address book provider might want to register one **MAPIUID** to use in the entry identifiers of its messaging user objects and a different **MAPIUID** to use for distribution lists. 
    
When there are multiple logon objects that are concurrently active, it makes sense to have unique **MAPIUID** structures for each one. This increases the accuracy with which MAPI matches entry identifiers to service providers and saves some work. When every logon object has its own unique identifier, MAPI can guarantee that any request it routes to a logon object can be handled by that object. When logon objects share **MAPIUID** structures, MAPI routes the request to the first logon object that is identified by the **MAPIUID**. If one of your logon objects receives a request that it cannot process because it does not handle the entry identifier, pass the request on to your next logon object before returning an error.
  
## See also



[Implementing Service Provider Logon](implementing-service-provider-logon.md)

