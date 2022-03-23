---
title: "PidTagMessageSubmissionId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageSubmissionId
api_type:
- HeaderDef
ms.assetid: 0a799fe5-04e2-4e1d-b0cd-9bdd2577d299
description: "Contains a MTS identifier for the MTA. This property is returned by the MTA upon successful completion of message submission."
---

# PidTagMessageSubmissionId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a message transfer system (MTS) identifier for the message transfer agent (MTA).
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_SUBMISSION_ID  <br/> |
|Identifier:  <br/> |0x0047  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

This property is returned by the MTA upon successful completion of message submission. Any future contact with the MTA regarding this message, such as requesting cancellation, uses the MTS identifier in this property.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXTNEF]](https://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
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

