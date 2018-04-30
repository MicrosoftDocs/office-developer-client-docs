---
title: "Adding a Message Service"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 1e626714-52dc-4141-9741-4d801f32d294
description: "Last modified: July 23, 2011"
---

# Adding a Message Service

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
 **To add a new message service to a profile and access the new message service**
  
Call [IMsgServiceAdmin2::CreateMsgServiceEx](imsgserviceadmin2-createmsgserviceex.md). **CreateMsgServiceEx** performs the following tasks: 
  
1. Copies all of the relevant information for the message service that is in the MAPISVC.INF file, creating a profile section for every provider section.
    
2. Calls the message service's entry point function, **MSGSERVICEENTRY**, with the  _ulContext_ parameter set to MSG_SERVICE_CREATE. 
    
3. Sets and retrieves the message service's **PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property.
    
 **To access any newly added message service**
  
1. Call [IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md) to retrieve the message service table. 
    
2. Call the message service table's [IMAPITable::Advise](imapitable-advise.md) method to register for table notifications. 
    
3. When MAPI sends a TABLE_ROW_ADDED notification, locate the entry identifier of the newly added message service in the [SRow](srow.md) structure included in the [TABLE_NOTIFICATION](table_notification.md) structure. 
    

