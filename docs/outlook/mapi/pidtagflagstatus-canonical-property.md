---
title: "PidTagFlagStatus Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFlagStatus
api_type:
- HeaderDef
ms.assetid: b5117360-0939-4535-83fe-3b4a240b5217
description: "Last modified: March 09, 2015"
---

# PidTagFlagStatus Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the flag state of the message object.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FLAG_STATUS  <br/> |
|Identifier:  <br/> |0x1090  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

This property must not exist on a meeting-related object, and it should not exist on a task object. When set on other message objects, this property must be set to one of the following values:
  
|**Numeric value**|**Name**|**Description**|
|:-----|:-----|:-----|
|Not present  <br/> |N/A  <br/> |Unflagged  <br/> |
|0x00000001  <br/> |followupComplete  <br/> |Flagged complete  <br/> |
|0x00000002  <br/> |followupFlagged  <br/> |Flagged  <br/> |
   
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOFLAG]](http://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

