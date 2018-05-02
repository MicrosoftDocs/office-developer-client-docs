---
title: "Message Service Tables"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b93ab837-3918-4427-b013-bedc6f5276e4
description: "Last modified: March 09, 2015"
 
 
---

# Message Service Tables

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
The message service table contains information about the message services in the current profile. There is one message service table for every MAPI session, implemented by MAPI and used by special purpose client applications that provide configuration support. 
  
The message service table is a static table.
  
Clients access the message service table by calling the [IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md) method. 
  
The following properties make up the required column set in the message service table:
  
|||
|:-----|:-----|
|**PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |**PR_INSTANCE_KEY** ( [PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |
|**PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md))  <br/> |**PR_SERVICE_DLL_NAME** ( [PidTagServiceDllName](pidtagservicedllname-canonical-property.md))  <br/> |
|**PR_SERVICE_ENTRY_NAME** ( [PidTagServiceEntryName](pidtagserviceentryname-canonical-property.md))  <br/> |**PR_SERVICE_NAME** ( [PidTagServiceName](pidtagservicename-canonical-property.md))  <br/> |
|**PR_SERVICE_SUPPORT_FILES** ( [PidTagServiceSupportFiles](pidtagservicesupportfiles-canonical-property.md))  <br/> |**PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md))  <br/> |
   
 **PR_DISPLAY_NAME** is the displayable name for the message service and the default sort key column. 
  
 **PR_INSTANCE_KEY** serves as the index column for the table, uniquely identifying a row. 
  
 **PR_RESOURCE_FLAGS** describes the message service's capabilities. 
  
 **PR_SERVICE_DLL_NAME** is the name of the DLL that contains the message service implementation. 
  
 **PR_SERVICE_ENTRY_NAME** is the name of the message service's entry point function that conforms to the [MSGSERVICEENTRY](msgserviceentry.md) prototype. 
  
 **PR_SERVICE_NAME** is a required entry in the **[Services]** section in MAPISVC.INF. The value for this property will never be changed or localized. **PR_SERVICE_NAME** can be used to programmatically identify the message service. 
  
 **PR_SERVICE_SUPPORT_FILES** is a list of files that must be installed with the message service. 
  
 **PR_SERVICE_UID** is a unique identifier for the message service. 
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

