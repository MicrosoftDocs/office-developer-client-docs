---
title: "PidLidRemoteTransport Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidRemoteTransport
api_type:
- COM
ms.assetid: b3b30d6a-05cd-4dd1-a162-20768f12e680
description: "Last modified: March 09, 2015"
---

# PidLidRemoteTransport Canonical Property

  
  
**Applies to**: Outlook 
  
Identifies what account the header item is associated with, primarily to implement the POP Leave on Server functionality. 
  
|||
|:-----|:-----|
|Associated Properties  <br/> |dispidRemoteXP  <br/> |
|Property set:  <br/> |PSETID_Remote  <br/> |
|Long ID (LID):  <br/> |0x00008F03  <br/> |
|Data type:  <br/> |PT_STRING8  <br/> |
|Area:  <br/> |Remote message  <br/> |
   
## Remarks

This property is relevant only on messages that have a message class of IPM.Remote. Microsoft Outlook keeps a mapping of various accounts that are downloading to a given store in a Folder Associated Information (FAI) message, but it could also keep this information in the registry.
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]] 
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

