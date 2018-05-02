---
title: "Provider Tables"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 99709a4c-cb52-436e-a322-02ded5d65ce5
description: "Last modified: March 09, 2015"
 
 
---

# Provider Tables

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
A provider table contains information about service providers. There are two different provider tables, both implemented by MAPI and used by clients. The first table, accessed by calling the [IMsgServiceAdmin::GetProviderTable](imsgserviceadmin-getprovidertable.md) method, holds information about all of the providers for the current profile. The second table, accessed through [IProviderAdmin::GetProviderTable](iprovideradmin-getprovidertable.md), creates a table that stores information about all of the service providers for a message service.
  
These two tables have another difference. The provider table available through **IMsgServiceAdmin::GetProviderTable** contains only rows that represent service providers while the table available through **IProviderAdmin::GetProviderTable** may include rows that represent additional information associated with a service provider. This extra information is added to the profile with the "Sections" keyword of MAPISVC.INF. When a provider has extra profile sections, it stores the **MAPIUID** values for these sections in the **PR_SERVICE_EXTRA_UIDS** ( [PidTagServiceExtraUids](pidtagserviceextrauids-canonical-property.md)) property. **PR_SERVICE_EXTRA_UIDS** is saved in the message service profile section. 
  
The following properties make up the required column set in both types of provider tables:
  
|||
|:-----|:-----|
|**PR_INSTANCE_KEY** ( [PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |**PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |
|**PR_PROVIDER_DISPLAY** ( [PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))  <br/> |**PR_PROVIDER_DLL_NAME** ( [PidTagProviderDllName](pidtagproviderdllname-canonical-property.md))  <br/> |
|**PR_PROVIDER_ORDINAL** ( [PidTagProviderOrdinal](pidtagproviderordinal-canonical-property.md))  <br/> |**PR_PROVIDER_UID** ( [PidTagProviderUid](pidtagprovideruid-canonical-property.md))  <br/> |
|**PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md))  <br/> |**PR_RESOURCE_TYPE** ( [PidTagResourceType](pidtagresourcetype-canonical-property.md))  <br/> |
|**PR_SERVICE_NAME** ( [PidTagServiceName](pidtagservicename-canonical-property.md))  <br/> |**PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md))  <br/> |
   
The provider table can be used to display the current transport order or to change it. To display the current order, build a restriction to retrieve only those rows with the **PR_RESOURCE_TYPE** property set to MAPI_TRANSPORT_PROVIDER. Then use **PR_PROVIDER_ORDINAL** as a sort key to sort the table and retrieve all the rows with either the [IMAPITable::QueryRows](imapitable-queryrows.md) method or the [HrQueryAllRows](hrqueryallrows.md) function. 
  
To change the transport order, apply the same restriction and retrieve the rows. Then create an array of values from the **PR_PROVIDER_UID** property that represents the unique identifiers for the transport providers. When the identifiers are in the desired order, pass them to the [IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md) method. 
  
After a provider table has been made available, it will not reflect subsequent changes, such as the addition or deletion of a provider.
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

