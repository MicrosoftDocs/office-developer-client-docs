---
title: "Reconfiguring a Transport Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3d466bde-b70d-44b6-ba03-6ad8353ec759
description: "Last modified: July 23, 2011"
 
 
---

# Reconfiguring a Transport Provider

  
  
**Applies to**: Outlook 
  
You can use a transport provider's status object to change some of the properties of the provider. The range of properties that can be changed depends on the properties that are included with the provider's property sheet and how those properties are defined. 
  
 **To reconfigure an active transport provider**
  
1. Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table. 
    
2. Locate the row for the transport provider to be reconfigured by creating a property restriction that matches **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) with the name of the target provider. 
    
3. Call [IMAPITable::FindRow](imapitable-findrow.md) to retrieve the appropriate row. 
    
4. Check that the STATUS_SETTINGS_DIALOG and STATUS_VALIDATE_STATE flags are set in the target transport provider's **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property. If STATUS_SETTINGS_DIALOG is not set, the transport provider does not display a configuration property sheet. If STATUS_VALIDATE_STATE is not set, you cannot perform dynamic reconfiguration.
    
5. If STATUS_SETTINGS_DIALOG is set, call [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) to display the transport provider's property sheet and allow the user to make changes. 
    
6. After the user has finished with the reconfiguration, call [IMAPIStatus::ValidateState](imapistatus-validatestate.md) if STATUS_VALIDATE_STATE is set, passing CONFIG_CHANGED. 
    

