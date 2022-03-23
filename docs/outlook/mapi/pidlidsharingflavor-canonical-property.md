---
title: "PidLidSharingFlavor Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidSharingFlavor
api_type:
- COM
ms.assetid: c91ab5c7-82ac-4895-bf54-2863ca5e2410
description: "Designates as a property of a sharing message for Outlook 2013 or Outlook 2016."
---

# PidLidSharingFlavor Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Designates as a property of a sharing message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingFlavor  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A18  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

The value of this property must be one of the following:
  
|**Value**|**Type of Sharing Message object**|
|:-----|:-----|
|0x00020310  <br/> |A sharing invitation for a special folder. |
|0x00000310  <br/> |A sharing invitation for a folder that is not a special folder. |
|0x00020500  <br/> |A sharing request. |
|0x00020710  <br/> |Both a sharing invitation for a special folder and a sharing request for the recipient's equivalent special folder. |
|0x00025100  <br/> |A sharing response denying a request. |
|0x00023310  <br/> |A sharing response accepting a request (also a type of sharing invitation). |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXSHARE]](https://msdn.microsoft.com/library/e4e5bd27-d5e0-43f9-a6ea-550876724f3d%28Office.15%29.aspx)
  
> Shares mailbox folders between clients.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

