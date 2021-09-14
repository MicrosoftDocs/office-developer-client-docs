---
title: "PidTagResourceMethods Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagResourceMethods
api_type:
- COM
ms.assetid: 60ebbcd5-b758-4c96-b8ec-089e0aae1a5f
description: "Last modified: March 09, 2015"
---

# PidTagResourceMethods Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags that indicate the methods in the **IMAPIStatus** interface that are supported by the status object. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RESOURCE_METHODS  <br/> |
|Identifier:  <br/> |0x3E02  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

This property indicates which of the methods in a status object's implementation of **IMAPIStatus** are supported. Status objects are allowed to return MAPI_E_NO_SUPPORT from unsupported methods. 
  
Clients use a status object's **PR_RESOURCE_METHODS** property to avoid making calls to unsupported methods. If the flag that corresponds to a particular method is set, the method exists and can be called. If that flag is clear, the method should not be called. 
  
The status objects implemented by MAPI support the following methods:
  
|**Status object**|**Supported methods**|
|:-----|:-----|
|MAPI subsystem  <br/> |**ValidateState** only  <br/> |
|MAPI address book  <br/> |**ValidateState** only  <br/> |
|MAPI spooler  <br/> |**ValidateState** and **FlushQueues** <br/> |
   
One or more of the following flags can be set in **PR_RESOURCE_METHODS**:
  
STATUS_CHANGE_PASSWORD 
  
> Indicates that the [IMAPIStatus::ChangePassword](imapistatus-changepassword.md) method is supported. 
    
STATUS_FLUSH_QUEUES 
  
> Indicates that the [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method is supported. 
    
STATUS_SETTINGS_DIALOG 
  
> Indicates that the [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method is supported. 
    
STATUS_VALIDATE_STATE 
  
> Indicates that the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method is supported. 
    
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

