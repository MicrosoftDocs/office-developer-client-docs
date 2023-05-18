---
title: "PidTagDiscardReason Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDiscardReason
api_type:
- HeaderDef
ms.assetid: 5004dc1f-6bd3-4764-b83c-d04d83161dba
description: "Contains a reason why a message transfer agent (MTA) has discarded a message to use in a nondelivery report for the message."
---

# PidTagDiscardReason Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a reason why a message transfer agent (MTA) has discarded a message. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DISCARD_REASON  <br/> |
|Identifier:  <br/> |0x0011  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

The reason contained in this property is used in a nondelivery report for the message.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagNonDeliveryReportReasonCode Canonical Property](pidtagnondeliveryreportreasoncode-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

