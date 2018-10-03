---
title: "PidTagPriority Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagPriority
api_type:
- COM
ms.assetid: 0f3a628f-5f8e-4716-98cc-868bd3400ba9
description: "Last modified: March 09, 2015"
---

# PidTagPriority Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the relative priority of a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PRIORITY  <br/> |
|Identifier:  <br/> |0x0026  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

This property and the **PR_IMPORTANCE** ([PidTagImportance](pidtagimportance-canonical-property.md)) property should not be confused. Importance indicates a value to users, while priority indicates the order or speed at which the message should be sent by the messaging system software. Higher priority usually indicates a higher cost. Higher importance usually is associated with a different display by the user interface.
  
The priority of a report message should be the same as the priority of the original message being reported.
  
This property can have exactly one of the following values:
  
PRIO_NONURGENT 
  
> The message is not urgent.
    
PRIO_NORMAL 
  
> The message has normal priority.
    
PRIO_URGENT 
  
> The message is urgent.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on email message objects.
    
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

