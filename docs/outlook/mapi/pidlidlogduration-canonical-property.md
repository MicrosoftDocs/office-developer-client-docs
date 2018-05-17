---
title: "PidLidLogDuration Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidLogDocumentSaved
api_type:
- COM
ms.assetid: 012a3f6e-fd16-4dc9-845d-2bf4cebeaa42
description: "Last modified: March 09, 2015"
---

# PidLidLogDuration Canonical Property

  
  
**Applies to**: Outlook 
  
Represents the duration, in minutes, of a journal message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidLogDuration  <br/> |
|Property set:  <br/> |PSETID_Log  <br/> |
|Long ID (LID):  <br/> |0x00008707  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Journal  <br/> |
   
## Remarks

The duration, in minutes, of the activity that must be the difference between the **dispidLogEnd** ( [PidLidLogEnd](pidlidlogend-canonical-property.md)) and **dispidLogStart** ( [PidLidLogStart](pidlidlogstart-canonical-property.md)) properties.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOJRNL]](http://msdn.microsoft.com/library/2aa04fd2-0f36-4ce4-9178-c0fc70aa8d43%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for journals.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

