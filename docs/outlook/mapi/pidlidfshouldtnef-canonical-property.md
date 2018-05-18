---
title: "PidLidFShouldTNEF Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidFShouldTNEF
api_type:
- COM
ms.assetid: 3cab23b6-f0e3-4703-a83b-12a617537651
description: "Last modified: March 09, 2015"
---

# PidLidFShouldTNEF Canonical Property

  
  
**Applies to**: Outlook 
  
Indicates whether to encode an item with Transport Neutral Encapsulation Format (TNEF). 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidFShouldTNEF  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085A5  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Run-time configuration  <br/> |
   
## Remarks

This property is set when Microsoft Word is set as the e-mail editor, and it sends an OLE object that is embedded in a Rich Text Format (RTF) stream.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]] 
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

