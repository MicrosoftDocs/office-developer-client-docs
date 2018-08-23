---
title: "PidTagRemoteValidateOk Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRemoteValidateOk
api_type:
- COM
ms.assetid: e336d2ec-57cb-4d08-bd6e-330ef7d9939e
description: "Last modified: March 09, 2015"
---

# PidTagRemoteValidateOk Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This property contains TRUE if the remote viewer is allowed to call the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_REMOTE_VALIDATE_OK  <br/> |
|Identifier:  <br/> |0x3E0D  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |MAPI Status  <br/> |
   
## Remarks

This property appears in the status table and offers some control over transport performance. It can be considered as another way of directing the remote viewer to idle. When it is set to TRUE, the remote viewer can call **IMAPIStatus::ValidateState** as often as desired. A value of FALSE indicates that the remote viewer cannot make any more calls. 
  
The transport provider usually sets this property dynamically, by setting the value to FALSE to disable additional calls when the transport provider has a sufficient amount of processing to perform. When the transport provider is done, it then sets the value to TRUE to allow the client application to make further **IMAPIStatus::ValidateState** calls. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

