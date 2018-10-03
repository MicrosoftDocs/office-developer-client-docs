---
title: "PidTagExpiryUnits Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExpiryUnits
api_type:
- HeaderDef
ms.assetid: f6a1ca22-cf4c-4e59-8846-6bd937fa8f6e
description: "Last modified: March 09, 2015"
---

# PidTagExpiryUnits Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes the unit of time when the **PR_EXPIRY_NUMBER** ([PidTagExpiryNumber](pidtagexpirynumber-canonical-property.md)) property multiplies.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXPIRY_UNITS  <br/> |
|Identifier:  <br/> |0x3FEE  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

This property, if set, must be one of the following values:
  
|||
|:-----|:-----|
|PidTagExpiryUnits  <br/> |Description (TimeOf)  <br/> |
|0x00000000  <br/> |Minutes, for example 60 seconds  <br/> |
|0x00000001  <br/> |Hours, for example 60x60 seconds  <br/> |
|0x00000002  <br/> |Day, for example 24x60x60 seconds  <br/> |
|0x00000003  <br/> |Week, for example 7x24x60x60 seconds  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
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

