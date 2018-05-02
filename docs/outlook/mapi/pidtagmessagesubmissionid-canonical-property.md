---
title: "PidTagMessageSubmissionId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMessageSubmissionId
api_type:
- HeaderDef
ms.assetid: 0a799fe5-04e2-4e1d-b0cd-9bdd2577d299
description: "Last modified: March 09, 2015"
---

# PidTagMessageSubmissionId Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains a message transfer system (MTS) identifier for the message transfer agent (MTA).
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_SUBMISSION_ID  <br/> |
|Identifier:  <br/> |0x0047  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

This property is returned by the MTA upon successful completion of message submission. Any future contact with the MTA regarding this message, such as requesting cancellation, uses the MTS identifier in this property.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXTNEF]](http://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

