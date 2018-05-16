---
title: "PidLidLogEnd Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidLogEnd
api_type:
- COM
ms.assetid: 621459ea-adf5-4420-9f0f-6f31b9b95508
description: "Last modified: March 09, 2015"
---

# PidLidLogEnd Canonical Property

  
  
**Applies to**: Outlook 
  
Represents the end date and time for the journal message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidLogEnd  <br/> |
|Property set:  <br/> |PSETID_Log  <br/> |
|Long ID (LID):  <br/> |0x00008708  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Journal  <br/> |
   
## Remarks

The time when the activity ended in Coordinated Universal Time The (UTC), which must be equal to the **dispidCommonEnd** ( [PidLidCommonEnd](pidlidcommonend-canonical-property.md)) property and greater than or equal to **dispidLogStart** ( [PidLidLogStart](pidlidlogstart-canonical-property.md)) property.
  
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

