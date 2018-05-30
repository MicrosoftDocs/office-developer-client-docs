---
title: "PidTagDeliverTime Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDeliverTime
api_type:
- HeaderDef
ms.assetid: da0ad17b-08ac-4c50-ac1d-13062b890dfd
description: "Last modified: March 09, 2015"
---

# PidTagDeliverTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the date and time when the original message was delivered. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DELIVER_TIME  <br/> |
|Identifier:  <br/> |0x0010  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property is a per-recipient property on a delivery report that indicates the time the original message was delivered to the messaging user for which the delivery report is being generated.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMAPISupport::StatusRecips](imapisupport-statusrecips.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

