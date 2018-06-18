---
title: "Configuring a Message Service"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d68892e3-7c87-4b3a-a691-bff92f83ed00
description: "Last modified: July 23, 2011"
 
 
---

# Configuring a Message Service

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To configure all the service providers in a message service**
  
- Call [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md). If all of the data necessary for configuration is available programmatically, you can choose whether or not to display a user interface. However, if some of the information for one or more providers is not available, make sure that you set the SERVICE_UI_ALLOWED or SERVICE_UI_ALWAYS flag. Suppressing a user interface when required configuration data is unavailable results in an unconfigured message service.
    
 **To configure a single service provider in a message service**
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the service provider's status object. 
    
2. Call [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) to display the service provider's property sheet. 
    
For more information about using status objects, see [Status Table and Status Objects](status-table-and-status-objects.md).
  

