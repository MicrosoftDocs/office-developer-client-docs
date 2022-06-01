---
title: "IProviderAdmin  IUnknown"
description: "Describes the properties and vtable order of members for IProviderAdmin IUnknown, which works with service providers in a message service."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IProviderAdmin
api_type:
- COM
ms.assetid: bdb4cdca-8dfd-4f90-9467-ec31cea3f518
---

# IProviderAdmin : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Works with service providers in a message service. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Provider administration objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
|Interface identifier:  <br/> |IID_IProviderAdmin  <br/> |
|Pointer type:  <br/> |LPPROVIDERADMIN  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[GetLastError](iprovideradmin-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error that occurred to the provider administration object. |
|[GetProviderTable](iprovideradmin-getprovidertable.md) <br/> |Provides access to the message service's provider table, a list of the service providers in the message service. |
|[CreateProvider](iprovideradmin-createprovider.md) <br/> |Adds a service provider to the message service. |
|[DeleteProvider](iprovideradmin-deleteprovider.md) <br/> |Deletes a service provider from the message service. |
|[OpenProfileSection](iprovideradmin-openprofilesection.md) <br/> |Opens a profile section from the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access. |
   
## Remarks

Clients can get a pointer to an **IProviderAdmin** interface by calling the [IMsgServiceAdmin::AdminProviders](imsgserviceadmin-adminproviders.md) method; service providers are passed an **IProviderAdmin** pointer when their message service's entry point function is called. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

