---
title: "Status Tables"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f2b2aca7-757f-4260-96a5-d0af55189711
description: "Last modified: March 09, 2015"
 
 
---

# Status Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The status table contains information relating to the state of the current session. There is one status table for every MAPI session that includes information provided by MAPI and by service providers. MAPI provides data for three rows: a row for the MAPI subsystem, a row for the MAPI spooler, and a row for the integrated address book. Because transport providers are required to supply status information to the status table, there is one row for every active transport provider. Address book and message store providers can choose whether to support the status table. 
  
Because each row is provided by a different resource, the set of columns can vary from row to row. There is a set of columns that every status object is required to supply and a set of columns that MAPI supplies. A service provider can add to these sets to expose provider-specific properties. For example, message store providers might add **PR_STORE_RECORD_KEY** ([PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md)) to supply clients with the identifier of their message store. Clients must have advance knowledge of the existence of this extra information to be able to use it. 
  
The following table lists the properties that must be in every status table row. The implementer of the status object provides some of the properties; others are computed by MAPI.
  
|**Properties provided by status object**|**Properties provided by MAPI**|
|:-----|:-----|
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |**PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md))  <br/> |
|**PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md))  <br/> |**PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md))  <br/> |
|**PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md))  <br/> |**PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md))  <br/> |
   
If the status object provides an identity, it should set **PR_IDENTITY_DISPLAY** ([PidTagIdentityDisplay](pidtagidentitydisplay-canonical-property.md)), **PR_IDENTITY_ENTRYID** ([PidTagIdentityEntryId](pidtagidentityentryid-canonical-property.md)), and **PR_IDENTITY_SEARCH_KEY** ([PidTagIdentitySearchKey](pidtagidentitysearchkey-canonical-property.md)), and include these properties in the table. 
  
Four properties are computed by MAPI for each status table row:
  
|||
|:-----|:-----|
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |**PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |**PR_ROWID** ([PidTagRowid](pidtagrowid-canonical-property.md))  <br/> |
   
MAPI assigns an entry identifier to the status row to enable clients to open the corresponding status object. A row identifier is also assigned to identify the row in the table as is an instance key to identify the data in the status object. The **PR_OBJECT_TYPE** property is set to MAPI_STATUS. 
  
To access the status table, clients call the [IMAPISession::GetStatusTable](imapisession-getstatustable.md) method. This call should not be made immediately upon startup. This is because **GetStatusTable** has to wait for the MAPI spooler to initialize the transport providers, an operation that is postponed until after the client has finished its logon. **GetStatusTable** is a relatively fast call after the MAPI spooler has completed its startup processing. 
  
Status table information can be used in a variety of ways, such as to access a status object, to determine whether a client is running in a connected or offline mode, and to monitor a provider's state. For example, clients can open a specific service provider's status object by passing the value of the **PR_ENTRYID** property to the [IMAPISession::OpenEntry](imapisession-openentry.md) method. The status object supports the **IMAPIStatus** interface, an interface that contains methods to change a service provider password, flush the message queue, display a configuration property sheet, or confirm status with a provider directly. Status table information can also be used to build a dialog box to inform clients of progress during a lengthy operation. 
  
Service providers who do support the status table use the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method to create and update their row. Whenever a change occurs to their row, all advise sink objects registered to receive status table notifications must be notified. Service providers can call the [IMAPISupport::Notify](imapisupport-notify.md) method if they are using the MAPI notification utility or call each advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method directly. 
  
## See also



[MAPI Tables](mapi-tables.md)

