---
title: "Adding or Deleting Providers in a Message Service"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 44bb4d34-ca96-4d5a-93fe-85e09bd7971d
description: "Last modified: July 23, 2011"
---

# Adding or Deleting Providers in a Message Service

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
To add or delete service providers in a message service, use the [IProviderAdmin : IUnknown](iprovideradminiunknown.md) interface. You can retrieve an **IProviderAdmin** pointer by calling [IMsgServiceAdmin::AdminProviders](imsgserviceadmin-adminproviders.md). The provider table, accessable through [IProviderAdmin::GetProviderTable](iprovideradmin-getprovidertable.md), lists information about the service providers currently installed in the message service. Clients and service providers can use the provider table to access the name of the provider DLL file, for example, or the **MAPIUID**, display name, and type of the provider as well as information about the message service. For more information, see [Provider Tables](provider-tables.md).
  
 **To add or delete a service provider in a message service**
  
1. Call the **AdminServices** method to access a message service administration object. 
    
2. Call [IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md) to access the message service table. 
    
3. Build a property restriction using an [SPropertyRestriction](spropertyrestriction.md) structure that matches **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) or **PR_SERVICE_NAME** ( [PidTagServiceName](pidtagservicename-canonical-property.md)) with the name of the message service to be modified. 
    
4. Call the message service table's [IMAPITable::FindRow](imapitable-findrow.md) method to locate the row in the table that represents the targeted message service. 
    
5. Call [IMsgServiceAdmin::AdminProviders](imsgserviceadmin-adminproviders.md) to retrieve an **IProviderAdmin** pointer. Pass the **PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md)) column from the message service table row as the  _lpUID_ parameter. 
    
6. Call [IProviderAdmin::GetProviderTable](iprovideradmin-getprovidertable.md) to access the provider table. 
    
7. Build a property restriction using an SPropertyRestriction structure that matches **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) or **PR_PROVIDER_DISPLAY** ( [PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md)) with the name of the service provider to be added or deleted. 
    
8. Call the provider table's [IMAPITable::FindRow](imapitable-findrow.md) method to locate the row in the table that represents the targeted service provider. 
    
9. Call [IProviderAdmin::CreateProvider](iprovideradmin-createprovider.md) to add the provider or [IProviderAdmin::DeleteProvider](iprovideradmin-deleteprovider.md) to remove it from the message service. For **CreateProvider**, pass the provider's **PR_DISPLAY_NAME** property as the  _lpszProvider_ parameter. For either method, pass the provider's **PR_SERVICE_UID** property as the  _lpUID_ parameter. After the service provider has been added or deleted, the change will not be apparent until a new session is created. 
    
Another technique for adding a service provider, specifically a message store provider, to a profile involves constructing an entry identifier for the provider. Because constructing an entry identifier requires knowledge of its format, this technique can only be used if the service provider has made its entry identifier format public. 
  
With the newly constructed entry identifier, a client can call [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md). MAPI automatically creates a profile section in the profile for the service provider, but does not add it to a message service. 
  
Some message services do not allow this type of dynamic modification; whether or not it is supported is up to the message service. Another feature that may or may not be supported is the ability to directly access a message service's private profile sections. If the message service you are using permits such access, it will publish the **GUID** that represents the private section in MAPISVC.INF. You can pass this **GUID** in a call to [IProviderAdmin::OpenProfileSection](iprovideradmin-openprofilesection.md) to access the profile section. 
  

