---
title: "IPropData  IMAPIProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPropData
api_type:
- COM
ms.assetid: 30b8ae9e-0c0c-4468-b286-29e083696fed
description: "Last modified: March 09, 2015"
---

# IPropData : IMAPIProp

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Provides the ability to retrieve and change the access for an object's properties. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Exposed by:  <br/> |Property data object  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers and client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIPropData  <br/> |
|Pointer type:  <br/> |LPPROPDATA  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[HrSetObjAccess](ipropdata-hrsetobjaccess.md) <br/> |Sets the access level for the object.  <br/> |
|[HrSetPropAccess](ipropdata-hrsetpropaccess.md) <br/> |Sets the access level and status for one or more of the object's properties.  <br/> |
|[HrGetPropAccess](ipropdata-hrgetpropaccess.md) <br/> |Retrieves the access level and status for one or more of the object's properties.  <br/> |
|[HrAddObjProps](ipropdata-hraddobjprops.md) <br/> |Adds one or more properties of type PT_OBJECT to the object.  <br/> |
   
## Remarks

The **IPropData::IMAPIProp** interface is implemented by MAPI and used primarily by service providers that access this implementation by calling the [CreateIProp](createiprop.md) function. 
  
For more information about access levels on objects and properties, see [Permissions for Objects and Properties](permissions-for-mapi-objects-and-properties.md).
  
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

