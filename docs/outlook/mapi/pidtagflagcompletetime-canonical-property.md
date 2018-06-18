---
title: "PidTagFlagCompleteTime Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFlagCompleteTime
api_type:
- HeaderDef
ms.assetid: effc738a-30f4-4a5e-b21d-04b50dad1f45
description: "Last modified: March 09, 2015"
---

# PidTagFlagCompleteTime Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the date and time in Coordinated Universal Time (UTC) that the message object was flagged as completed.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FLAG_COMPLETE_TIME  <br/> |
|Identifier:  <br/> |0x1091  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

This property is deleted if the message object is not flagged complete. The time's smallest resolution must be minutes (the value must be a multiple of 600,000,000). This property must not exist if the object is a meeting-related object, and it should not exist on a task object.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOFLAG]](http://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

