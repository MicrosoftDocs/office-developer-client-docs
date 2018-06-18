---
title: "PidTagToDoItemFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagToDoItemFlags
api_type:
- COM
ms.assetid: bb7ccb45-ce08-4d22-9259-db15cd267e34
description: "Last modified: March 09, 2015"
---

# PidTagToDoItemFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Represents a To-Do item's flagged condition.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_TODO_ITEM_FLAGS  <br/> |
|Identifier:  <br/> |0x0E2B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

This property is a bit field in which each bit should be set to 1 if the associated condition in the following table applies, otherwise 0.
  
||||
|:-----|:-----|:-----|
|Numeric value  <br/> |Name  <br/> |Description  <br/> |
|Not present  <br/> |N/A  <br/> |Unflagged  <br/> |
|1  <br/> |todoTimeFlagged  <br/> |Object is time flagged  <br/> |
|8  <br/> |todoRecipientFlagged  <br/> |Should only be set on a draft message object, and it means that the object is flagged for recipients.  <br/> |
   
All bits that are not specified in the table are reserved. They must be ignored, but should be preserved if they are set.
  
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

