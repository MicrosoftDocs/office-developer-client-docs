---
title: "PidTagImportance Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagImportance
api_type:
- HeaderDef
ms.assetid: 274dd444-a863-4b53-bdbc-3763c375c43c
description: "Last modified: March 09, 2015"
---

# PidTagImportance Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a value that indicates the message sender's opinion of the importance of a message. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_IMPORTANCE  <br/> |
|Identifier:  <br/> |0x0017  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property and the **PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md)) property should not be confused. Importance indicates a value to users, while priority indicates the order or speed at which the message should be sent by the messaging system software. Higher priority usually indicates a higher cost. Higher importance usually is associated with a different display by the user interface. 
  
This property can have exactly one of the following values:
  
IMPORTANCE_LOW 
  
> The message has low importance.
    
IMPORTANCE_HIGH 
  
> The message has high importance.
    
IMPORTANCE_NORMAL 
  
> The message has normal importance.
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

