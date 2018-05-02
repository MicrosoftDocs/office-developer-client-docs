---
title: "Copying a Message Service"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 01e8ad76-973a-42fa-96aa-f41aabc12b4f
description: "Last modified: July 23, 2011"
 
 
---

# Copying a Message Service

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
 **To copy a message service to a profile**
  
- Call [IMsgServiceAdmin::CopyMsgService](imsgserviceadmin-copymsgservice.md).
    
When a message service is copied, the new instance of the service is configured in exactly the same way as the original. Sometimes **CopyMsgService** returns the error MAPI_E_ACCESS_DENIED. The most common cause of this error return is a message service that does not allow itself to be duplicated. 
  

