---
title: "IPropData  IMAPIProp"
description: "IPropData IMAPIProp provides the ability to retrieve and change the access for an object's properties."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IPropData
api_type:
- COM
ms.assetid: 30b8ae9e-0c0c-4468-b286-29e083696fed
---

# IPropData : IMAPIProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides the ability to retrieve and change the access for an object's properties. 
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Exposed by:  <br/> |Property data object  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers and client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIPropData  <br/> |
|Pointer type:  <br/> |LPPROPDATA  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[HrSetObjAccess](ipropdata-hrsetobjaccess.md) <br/> |Sets the access level for the object. |
|[HrSetPropAccess](ipropdata-hrsetpropaccess.md) <br/> |Sets the access level and status for one or more of the object's properties. |
|[HrGetPropAccess](ipropdata-hrgetpropaccess.md) <br/> |Retrieves the access level and status for one or more of the object's properties. |
|[HrAddObjProps](ipropdata-hraddobjprops.md) <br/> |Adds one or more properties of type PT_OBJECT to the object. |
   
## Remarks

The **IPropData::IMAPIProp** interface is implemented by MAPI and used primarily by service providers that access this implementation by calling the [CreateIProp](createiprop.md) function. 
  
For more information about access levels on objects and properties, see [Permissions for Objects and Properties](permissions-for-mapi-objects-and-properties.md).
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

