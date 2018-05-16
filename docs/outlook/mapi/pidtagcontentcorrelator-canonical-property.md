---
title: "PidTagContentCorrelator Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContentCorrelator
api_type:
- HeaderDef
ms.assetid: 0bf78879-2f9f-4c29-b1f4-2f4882d8464d
description: "Last modified: March 09, 2015"
---

# PidTagContentCorrelator Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a value the message sender can use to match a report with the original message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTENT_CORRELATOR  <br/> |
|Identifier:  <br/> |0x0007  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

The contents of the binary string are defined by the message originator. If set on an outgoing message, this property should be copied onto any reports generated in response to the message.
  
## Related Resources

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

