---
title: "Permissions for MAPI Objects and Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 32669cbe-5460-4043-99cc-c609608f48da
description: "Last modified: July 23, 2011"
 
 
---

# Permissions for MAPI Objects and Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Access permission, or the set of permissable operations, can be a characteristic of MAPI objects and of individual properties supported by those objects. Object access is determined by an object's parent. For a message, its folder determines access permissions. For a messaging user or distribution list, its address book container makes this determination. When an object such as a message resides in two folders, the permissions for the two copies of the object can be different. 
  
Clients using these objects can request the highest level of access permitted for the object by setting the MAPI_BEST_ACCESS flag on the [IMAPISession::OpenEntry](imapisession-openentry.md) call. Depending on the service provider implementing the object, the client may or may not be granted the level of access necessary. Clients can determine the level of access that they were granted by calling the object **GetProps** method to retrieve the **PR_ACCESS** ([PidTagAccess](pidtagaccess-canonical-property.md)) property. However, because the service provider must dynamically generate the value for this property, it is recommended that clients retrieve it only when necessary. 
  
To determine whether a container such as a folder, address book container, or distribution list allows modification, call its **GetProps** method to retrieve the **PR_ACCESS_LEVEL** ([PidTagAccessLevel](pidtagaccesslevel-canonical-property.md)) property. Container level access affects clients in terms of how they display their user interfaces. It also impacts the implementers of objects within containers in terms of their user interface display and their general implementation. 
  
Access to a particular property is determined by the property schema set up by MAPI for the object that owns the property. Property schemas specify the set of required and optional properties for an object and their access permission. Unlike object access which is determined by the object's parent, property access is global. Every object, regardless of the access requirements of the object's parent, has the same permissions for the property as determined by the schema.
  
When a property is read-only, it will always be available with a **GetProps** or **OpenProperty** call. However, depending on the implementation of the object supporting the property, there are two possible outcomes for the **SetProps** method for modifying a property and the **DeleteProps** method for removing it: 
  
- Fail and return MAPI_E_NO_ACCESS
    
- Succeed with no action taken
    
Property and object access can also be retrieved or set by using the [IPropData](ipropdataimapiprop.md) interface that inherits from the **IMAPIProp** interface. MAPI provides an implementation of **IPropData** that is based on data in memory. Service providers can use **IPropData** to implement **IMAPIProp** in certain circumstances, such as for their status object or if they are using a database that does not have built-in transactions. **IPropData** works exclusively in memory, making it unnecessary to lock and unlock data. 
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

