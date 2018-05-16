---
title: "PidLidSharingProviderUrl Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSharingProviderUrl
api_type:
- COM
ms.assetid: d217ab33-d697-4d27-a962-08d551d301f0
description: "Last modified: March 09, 2015"
---

# PidLidSharingProviderUrl Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the URL that is related to the sharing provider and identified by the **dispidSharingProviderGuid** ( [PidLidSharingProviderGuid](pidlidsharingproviderguid-canonical-property.md)) property. This is a property of a sharing message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingProviderUrl  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A03  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

This property is generally used to provide more information about the sharing provider, but should be ignored.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXSHARE]](http://msdn.microsoft.com/library/e4e5bd27-d5e0-43f9-a6ea-550876724f3d%28Office.15%29.aspx)
  
> Shares mailbox folders between clients.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

