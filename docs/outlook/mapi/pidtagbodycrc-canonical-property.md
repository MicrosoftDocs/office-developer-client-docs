---
title: "PidTagBodyCrc Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagBodyCrc
api_type:
- HeaderDef
ms.assetid: 6efe9dc3-e988-4042-ab02-2863b5e0f294
description: "Last modified: March 09, 2015"
---

# PidTagBodyCrc Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a cyclic redundancy check (CRC) value on the message text.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_BODY_CRC  <br/> |
|Identifier:  <br/> |0x0E1C  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

The message store can use any CRC algorithm that generates a PT_LONG value. It must compute this property as part of the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method when the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property has been set for the first time and whenever it has been subsequently modified.
  
A client application uses **PR_BODY_CRC** to aid in comparing message text strings contained in **PR_BODY** properties or their variants. Using this property, the client can quickly and easily detect when the message text has changed. It can realize significant performance gains by using **PR_BODY_CRC** instead of obtaining **PR_BODY** from the message store and comparing it with a local version. 
  
## Related resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

