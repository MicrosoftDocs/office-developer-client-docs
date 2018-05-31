---
title: "PidLidSharingCapabilities Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSharingCapabilities
api_type:
- COM
ms.assetid: 86b3eab2-2594-4204-aedf-8ce2ee3b81ce
description: "Last modified: March 09, 2015"
---

# PidLidSharingCapabilities Canonical Property

  
  
**Applies to**: Outlook 
  
Designates as a property of a sharing message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingCaps  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A17  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

This property must be set to one of the following values:
  
|**Value**|**Scenario**|
|:-----|:-----|
|0x00040290  <br/> |This Sharing Message object relates to a special folder.  <br/> |
|0x000402B0  <br/> |This Sharing Message object does not relate to a special folder.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXSHARE]](http://msdn.microsoft.com/library/e4e5bd27-d5e0-43f9-a6ea-550876724f3d%28Office.15%29.aspx)
  
> Shares mailbox folders between clients.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

