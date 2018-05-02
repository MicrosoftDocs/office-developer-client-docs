---
title: "PidTagDeferredSendUnits Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDeferredSendUnits
api_type:
- HeaderDef
ms.assetid: 2386be9f-18c9-4949-a2aa-efc8e212801c
description: "Last modified: March 09, 2015"
---

# PidTagDeferredSendUnits Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Specifies the unit of time by which the **PR_DEFERRED_SEND_NUMBER** ( [PidTagDeferredSendNumber](pidtagdeferredsendnumber-canonical-property.md)) property value should be multiplied.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DEFERRED_SEND_UNITS  <br/> |
|Identifier:  <br/> |0x3FEC  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

If set, this property must have one of the following values:
  
|||
|:-----|:-----|
|**PidTagDeferredSendUnits** <br/> |Description  <br/> |
|0  <br/> |Minutes, for example 60 seconds  <br/> |
|1  <br/> |Hours, for example 60x60 seconds  <br/> |
|2  <br/> |Day, for example 24x60x60 seconds  <br/> |
|3  <br/> |Week, for example 7x24x60x60 seconds  <br/> |
   
## Related Resources

### Protocol Specifications

[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
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

