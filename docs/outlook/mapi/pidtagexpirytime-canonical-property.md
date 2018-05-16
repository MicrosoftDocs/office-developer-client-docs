---
title: "PidTagExpiryTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExpiryTime
api_type:
- HeaderDef
ms.assetid: 6e4d4ee9-c6b1-4987-b02e-684c2af3d21c
description: "Last modified: March 09, 2015"
---

# PidTagExpiryTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the date and time when the messaging system can invalidate the content of a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXPIRY_TIME  <br/> |
|Identifier:  <br/> |0x0015  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property is used to direct the messaging system in handling delivered interpersonal messages. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on e-mail messages.
    
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

