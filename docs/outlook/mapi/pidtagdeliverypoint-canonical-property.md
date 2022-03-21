---
title: "PidTagDeliveryPoint Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDeliveryPoint
api_type:
- HeaderDef
ms.assetid: 715a9dbd-78f8-41e1-a76e-29448d06ec19
description: "Last modified: March 09, 2015"
---

# PidTagDeliveryPoint Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the nature of the functional entity by means of which a message was or would have been delivered to the recipient. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DELIVERY_POINT  <br/> |
|Identifier:  <br/> |0x0C07  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI recipient  <br/> |
   
## Remarks

This property can have exactly one of the following values: 
  
MAPI_MH_DP_ML 
  
> Delivered to a distribution list, a delivery point which in turn may distribute the message to many recipients.
    
MAPI_MH_DP_MS 
  
> Delivered to a message store instead of directly to a recipient.
    
MAPI_MH_DP_OTHER_AU 
  
> Delivered to an access unit (AU) other than a physical delivery access unit (PDAU), such as a FAX system.
    
MAPI_MH_DP_PDAU 
  
> Delivered to a physical delivery access unit, such as a human postal carrier.
    
MAPI_MH_DP_PDS_PATRON 
  
> Delivered to a physical delivery system patron, such as a conventional postal mailbox.
    
MAPI_MH_DP_PRIVATE_UA 
  
> Delivered to a private user agent (UA), such as a client in an in-house messaging system.
    
MAPI_MH_DP_PUBLIC_UA 
  
> Delivered to a public user agent, or public service provider.
    
The default value is MAPI_MH_DP_PRIVATE_UA, that is, a MAPI client. 
  
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

