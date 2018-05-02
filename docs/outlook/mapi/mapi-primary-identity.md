---
title: "MAPI Primary Identity"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 8787a873-6752-4b17-8ea3-8fed793e1371
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Primary Identity

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Most MAPI sessions have a particular service provider that supplies the primary identity for the session. Typically, it is an address book provider, which supplies identity through one of its messaging user objects or distribution lists. In fact, MAPI recommends that message services that include an address book provider use one of its objects for the primary identity. When a service provider that belongs to a message service supplies the primary identity, all of the other service providers in the message service share this identity.
  
The MAPISVC.INF configuration file has entries relating to identity at both the message service and service provider level. Message service sections must include an entry that states whether or not the service can supply the primary identity; service provider sections include a similar entry only when the provider can supply an identity.
  
The following table lists the entries that appear in the message service and service provider sections in the MAPISVC.INF file.
  
|**Primary identity supplier**|**PR_RESOURCE_FLAGS setting**|
|:-----|:-----|
|Message service  <br/> | `SERVICE_PRIMARY_IDENTITY` <br/> |
|Not the message service  <br/> | `SERVICE_NO_PRIMARY_IDENTITY` <br/> |
|Service provider  <br/> | `STATUS_PRIMARY_IDENTITY` <br/> |
   
Although multiple message services can declare their ability to provide a session's primary identity, only one message service is selected to do so. This selection can occur:
  
- When a profile is created.
    
- When a client calls **IMsgServiceAdmin::SetPrimaryIdentity** to explicitly establish a particular message service as the provider of the session identity. For more information. See [IMsgServiceAdmin::SetPrimaryIdentity](imsgserviceadmin-setprimaryidentity.md).
    
When a profile is created, MAPI designates the first message service to be configured that includes a provider with the STATUS_PRIMARY_IDENTITY flag set in its **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property to supply the primary identity. Within the designated message service, the first provider to be configured with this resource flag set is chosen to provide the identity for the service. The STATUS_PRIMARY_IDENTITY flag is cleared for all other providers in the designated service and other message services in the profile. If at any time the provider supplying primary identity is removed from the profile, MAPI assigns the role to the next provider to be configured that can supply identity. This is determined by the appearance of the  `PR_RESOURCE_FLAGS=STATUS_PRIMARY_IDENTITY` entry in the provider's section in MAPISVC.INF. 
  
When a client calls a message service's **IMsgServiceAdmin::SetPrimaryIdentity** method, it specifies the MAPIUID for a service provider within the target service. For more information, see [MAPIUID](mapiuid.md). The service provider represented by the **MAPIUID** is assigned to supply the primary identity for the message service and for the session, and all of the other providers in the service will share this identity. 
  
Every provider in the message service responsible for supplying the primary identity updates its row in the status table to include the following properties.
  
|**Primary identity property**|**Set to**|
|:-----|:-----|
|**PR_IDENTITY_DISPLAY** ( [PidTagIdentityDisplay](pidtagidentitydisplay-canonical-property.md))  <br/> |Display name of the object supplying the primary identity.  <br/> |
|**PR_IDENTITY_SEARCH_KEY** ( [PidTagIdentitySearchKey](pidtagidentitysearchkey-canonical-property.md))  <br/> |Search key for the object supplying the primary identity.  <br/> |
|**PR_IDENTITY_ENTRYID** ( [PidTagIdentityEntryId](pidtagidentityentryid-canonical-property.md))  <br/> |Entry identifier for the object supplying the primary identity.  <br/> |
   
 **To retrieve the entry identifier for the object supplying the primary identity**
  
- Call the **IMAPISession::QueryIdentity** method. For more information, see [IMAPISession::QueryIdentity](imapisession-queryidentity.md). **QueryIdentity** searches the status table for the row that contains the value STATUS_PRIMARY_IDENTITY in its **PR_RESOURCE_FLAGS** column and returns the corresponding **PR_IDENTITY_ENTRYID** as the entry identifier for the primary identity. 
    

