---
title: "IProviderAdmin  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin
api_type:
- COM
ms.assetid: bdb4cdca-8dfd-4f90-9467-ec31cea3f518
description: "Last modified: March 09, 2015"
---

# IProviderAdmin : IUnknown

  
  
**Applies to**: Outlook 
  
Works with service providers in a message service. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Provider administration objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
|Interface identifier:  <br/> |IID_IProviderAdmin  <br/> |
|Pointer type:  <br/> |LPPROVIDERADMIN  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](iprovideradmin-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error that occurred to the provider administration object.  <br/> |
|[GetProviderTable](iprovideradmin-getprovidertable.md) <br/> |Provides access to the message service's provider table, a list of the service providers in the message service.  <br/> |
|[CreateProvider](iprovideradmin-createprovider.md) <br/> |Adds a service provider to the message service.  <br/> |
|[DeleteProvider](iprovideradmin-deleteprovider.md) <br/> |Deletes a service provider from the message service.  <br/> |
|[OpenProfileSection](iprovideradmin-openprofilesection.md) <br/> |Opens a profile section from the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access.  <br/> |
   
## Remarks

Clients can get a pointer to an **IProviderAdmin** interface by calling the [IMsgServiceAdmin::AdminProviders](imsgserviceadmin-adminproviders.md) method; service providers are passed an **IProviderAdmin** pointer when their message service's entry point function is called. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

