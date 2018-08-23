---
title: "PidTagResourceFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagResourceFlags
api_type:
- COM
ms.assetid: 69be9ad3-006a-459e-9cd4-eb3f609d71ad
description: "Last modified: March 09, 2015"
---

# PidTagResourceFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags for message services and providers.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RESOURCE_FLAGS  <br/> |
|Identifier:  <br/> |0x3009  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property describes the characteristics of a message service, a service provider, or a status object. The flags that are set for this property depend on its context. For example, some flags are valid only for status objects and other flags only for columns in the message service table. 
  
The flags are of three classes: static, modifiable, and dynamic. Static flags are set by MAPI from data in MAPISVC.INF and never altered. Modifiable flags are set by MAPI from MAPISVC.INF but can be subsequently changed. Dynamic flags can be set and reset by MAPI methods.
  
For a message service, one or more of the following flags can be set in this property:
  
SERVICE_CREATE_WITH_STORE 
  
> Reserved. Do not use.
    
SERVICE_DEFAULT_STORE 
  
> Dynamic. The message service contains the default store. A user interface should be displayed prompting the user for confirmation before deleting or moving this service out of the profile. 
    
SERVICE_NO_PRIMARY_IDENTITY 
  
> Static. The service level flag that should be set to indicate that none of the providers in the message service can be used to supply an identity. Either this flag or SERVICE_PRIMARY_IDENTITY should be set, but not both.
    
SERVICE_PRIMARY_IDENTITY 
  
> Modifiable. The corresponding message service contains the provider used for the primary identity for this session. Use [IMsgServiceAdmin::SetPrimaryIdentity](imsgserviceadmin-setprimaryidentity.md) to set this flag. Either this flag or SERVICE_NO_PRIMARY_IDENTITY should be set, but not both. 
    
SERVICE_SINGLE_COPY 
  
> Static. Any attempt to create or copy this message service into a profile where the service already exists will fail. To create a single copy message service add the **PR_RESOURCE_FLAGS** property to the service's section in MAPISVC.INF and set this flag. 
    
For a service provider, one or more of the following flags can be set in **PR_RESOURCE_FLAGS**:
  
HOOK_INBOUND 
  
> Static. The spooler hook needs to process inbound messages.
    
HOOK_OUTBOUND 
  
> Static. The spooler hook needs to process outbound messages. 
    
STATUS_DEFAULT_OUTBOUND 
  
> Modifiable. This identity should be applied to outbound messages if the profile contains multiple instances of this transport provider. This can happen if multiple instances of a single transport provider appear in the profile.
    
STATUS_DEFAULT_STORE 
  
> Modifiable. This message store is the default store for the profile. 
    
STATUS_NEED_IPM_TREE 
  
> Dynamic. The standard folders in this message store, including the interpersonal message (IPM) root folder, have not yet been verified. MAPI sets and clears this flag. 
    
STATUS_NO_DEFAULT_STORE 
  
> Static. This message store is incapable of becoming the default message store for the profile.
    
STATUS_NO_PRIMARY_IDENTITY 
  
> Static. This provider does not furnish an identity in its status row. Either this flag or STATUS_PRIMARY_IDENTITY must be set.
    
STATUS_OWN_STORE 
  
> Static. This transport provider is tightly coupled with a message store and furnishes the **PR_OWN_STORE_ENTRYID** ([PidTagOwnStoreEntryId](pidtagownstoreentryid-canonical-property.md)) property in its status row.
    
STATUS_PRIMARY_IDENTITY 
  
> Modifiable. This provider furnishes the primary identity for the session; the entry identifier for the object furnishing the identity is returned from [IMAPISession::QueryIdentity](imapisession-queryidentity.md). Either this flag or **STATUS_NO_PRIMARY_IDENTITY** must be set. 
    
STATUS_PRIMARY_STORE 
  
> Modifiable. This message store is to be used when a client application logs on. Once opened, this store should be set as the default store for the profile. 
    
STATUS_SECONDARY_STORE 
  
> Modifiable. This message store is to be used if the primary store is not available when a client application logs on. Once opened, this store should be set as the default store for the profile. 
    
STATUS_SIMPLE_STORE 
  
> Dynamic. This message store will be used by Simple MAPI as its default message store.
    
STATUS_TEMP_SECTION 
  
> Dynamic. This message store should not be published in the message store table and will be deleted from the profile after logoff. 
    
STATUS_XP_PREFER_LAST 
  
> Static. This transport expects to be the last transport selected to send a message when multiple transport providers are able to transmit the message.
    
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md)
  
[PidTagIdentityEntryId Canonical Property](pidtagidentityentryid-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

