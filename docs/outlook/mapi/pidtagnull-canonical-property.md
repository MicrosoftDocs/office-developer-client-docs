---
title: "PidTagNull Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagNull
api_type:
- HeaderDef
ms.assetid: 192cdab8-c615-47b9-9f04-a1414eaf0c77
description: "Last modified: March 09, 2015"
---

# PidTagNull Canonical Property

  
  
**Applies to**: Outlook 
  
Represents a null value or setting of a property or reserves array space.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_NULL  <br/> |
|Identifier:  <br/> |0x0000  <br/> |
|Data type:  <br/> |PT_NULL  <br/> |
|Area:  <br/> |Common  <br/> |
   
## Remarks

This property is used to reserve space in arrays of [SPropValue](spropvalue.md) structures. It is used in an array of [SPropTagArray](sproptagarray.md) structures to tell the method to reserve space in the returned array of **SPropValue** structures. This allows for computed properties to be filled in an inexpensive way. 
  
For more information, see [MAPI Property Type Overview](mapi-property-type-overview.md).
  
## Related resources

### Protocol specifications

[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on contacts and personal distribution lists.
    
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

