---
title: "MAPI Status Objects"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 38310619-1b1d-4934-8533-d0612676c0b0
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Status Objects

  
  
**Applies to**: Outlook 
  
Status objects report information about MAPI resources. For example, a service provider, the MAPI send/receive process, or the address book.
  
There is a status object supplying information about each individual service provider in the current profile. MAPI is responsible for implementing status objects for the subsystem, the MAPI send/receive process, and the address book. The subsystem status object supplies global information. The status object for the integrated address book supplies the status of all address book providers currently operating.
  
Every status object is included in the status table, a table maintained by MAPI that provides clients with all of the status information for the session. For more information, see [Status Tables](status-tables.md). Clients can access a particular status object either through the table or, for a service provider, through its logon object. For example, to access an address book provider's status object, a client can call **IABLogon::OpenStatusEntry**. For more information, see [IABLogon::OpenStatusEntry](iablogon-openstatusentry.md).
  
Clients can use status objects to:
  
- Learn about the state of a session.
    
- Monitor a service provider.
    
- Control message transmission.
    
- View or change a resource's configuration and status.
    
Every status object implements the **IMAPIStatus** interface. For more information, see [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md). However, not every status object fully supports every **IMAPIStatus** method. Because there is variation in the methods that are supported by a status object, clients need to learn about a particular status object before they can use it. Status objects are required to publish information about their features in the following three properties: 
  
 **PR_RESOURCE_METHODS** ( [PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) 
  
 **PR_RESOURCE_TYPE** ( [PidTagResourceType](pidtagresourcetype-canonical-property.md)) 
  
 **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) 
  
For more information about implementing a status object, see [Status Object Implementation](status-object-implementation.md). For more information about using a status object, see [Status Table and Status Objects](status-table-and-status-objects.md).
  

