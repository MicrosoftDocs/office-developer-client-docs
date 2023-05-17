---
title: "IMAPIStatus  IMAPIProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIStatus
api_type:
- COM
ms.assetid: 17b2aa43-0267-45b6-8c57-11b7a5c67333
description: "Provides status information about the MAPI subsystem, the integrated address book, and the MAPI spooler."
---

# IMAPIStatus : IMAPIProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides status information about the MAPI subsystem, the integrated address book, and the MAPI spooler. A service provider implements **IMAPIStatus** to supply information about its own status. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Status objects  <br/> |
|Implemented by:  <br/> |Service providers and MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIStatus  <br/> |
|Pointer type:  <br/> |LPMAPISTATUS  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

|Property |Value |
|:-----|:-----|
|[ValidateState](imapistatus-validatestate.md) <br/> |Confirms the external status information available for the MAPI resource or the service provider. |
|[SettingsDialog](imapistatus-settingsdialog.md) <br/> |Displays a property sheet that enables the user to change a service provider's configuration. |
|[ChangePassword](imapistatus-changepassword.md) <br/> |Modifies a service provider's password without displaying a user interface. |
|[FlushQueues](imapistatus-flushqueues.md) <br/> |Forces all messages waiting to be sent or received to be immediately uploaded or downloaded. |
   
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_PROVIDER_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md))  <br/> |Read-only  <br/> |
   
## Remarks

The status objects that MAPI implements support the following methods:
  
|**Status object**|**Supported methods**|
|:-----|:-----|
|MAPI subsystem  <br/> |**ValidateState** only  <br/> |
|MAPI address book  <br/> |**ValidateState** only  <br/> |
|MAPI spooler  <br/> |**ValidateState** and **FlushQueues** <br/> |
   
The status objects that MAPI implements are required to have a read-only version of the methods of the [IMAPIProp](imapipropiunknown.md) interface and to support the **ValidateState** method. Transport providers should also support **FlushQueues**. All providers should support **SettingsDialog**; support for **ChangePassword** is optional. 
  
Clients use status objects to perform configuration and to learn about the state of the session. They access a status object by calling the **OpenStatusEntry** method of a service provider logon object or the [IMAPISession::GetStatusTable](imapisession-getstatustable.md) method to retrieve the status object. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

