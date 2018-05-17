---
title: "Deleting a Message Service"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 346608d7-f7de-497e-9852-4d4d7696177e
description: "Last modified: July 23, 2011"
 
 
---

# Deleting a Message Service

  
  
**Applies to**: Outlook 
  
 **To delete a message service from a profile**
  
1. Call **IMAPISession::GetMsgServiceTable** to access the message service table. 
    
2. Locate the row for the message service and pass its **PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md)) column in the  _lpuid_ parameter to [IMsgServiceAdmin::DeleteMsgService](imsgserviceadmin-deletemsgservice.md). 
    
 **DeleteMsgService** calls the message service's entry point function with the  _ulContext_ parameter set to MSG_SERVICE_DELETE. Message services perform any clean up tasks at this time before they are removed from the profile. 
  

