---
title: "PidLidSharingProviderGuid Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidSharingProviderGuid
api_type:
- COM
ms.assetid: 103c9cf2-42fb-4fa5-b9c2-8a92725d3097
description: "Specifies the sharing provider globally unique identifier (GUID). This is a property of a sharing message."
---

# PidLidSharingProviderGuid Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the sharing provider globally unique identifier (GUID). This is a property of a sharing message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingProviderGuid  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A01  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

The value of this property must be set to "%xAE.F0.06.00.00.00.00.00.C0.00.00.00.00.00.00.46". 
  
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

