---
title: "PidTagDeferredSendUnits Canonical Property"
description: Outlines the PidTagDeferredSendUnits canonical property, which specifies the unit of time by which the PR_DEFERRED_SEND_NUMBER value should be multiplied.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDeferredSendUnits
api_type:
- HeaderDef
ms.assetid: 2386be9f-18c9-4949-a2aa-efc8e212801c
---

# PidTagDeferredSendUnits Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the unit of time by which the **PR_DEFERRED_SEND_NUMBER** ([PidTagDeferredSendNumber](pidtagdeferredsendnumber-canonical-property.md)) property value should be multiplied.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_DEFERRED_SEND_UNITS  <br/> |
|Identifier:  <br/> |0x3FEC  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

If set, this property must have one of the following values:
  
|**PidTagDeferredSendUnits** <br/> |Description  <br/> |
|:-----|:-----|
|0  <br/> |Minutes, for example 60 seconds  <br/> |
|1  <br/> |Hours, for example 60x60 seconds  <br/> |
|2  <br/> |Day, for example 24x60x60 seconds  <br/> |
|3  <br/> |Week, for example 7x24x60x60 seconds  <br/> |
   
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

