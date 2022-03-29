---
title: "PidTagRequestedDeliveryMethod Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRequestedDeliveryMethod
api_type:
- COM
ms.assetid: cc55089b-e389-405e-8174-f5b5ec352f78
description: "This property contains a binary array of delivery methods (service providers), in the order of a message sender's preference."
---

# PidTagRequestedDeliveryMethod Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This property contains a binary array of delivery methods (service providers), in the order of a message sender's preference.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_REQUESTED_DELIVERY_METHOD  <br/> |
|Identifier:  <br/> |0x0C18  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI Recipient  <br/> |
   
## Remarks

The array contained in the this property consists of ASN.1 identifiers for each of the service providers.
  
## Related resources

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

