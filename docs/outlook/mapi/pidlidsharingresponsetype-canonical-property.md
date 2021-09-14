---
title: "PidLidSharingResponseType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidSharingResponseType
api_type:
- COM
ms.assetid: c27b1239-3612-4bb3-9f22-4b89ee9900cd
description: "Last modified: March 09, 2015"
---

# PidLidSharingResponseType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the type of response with which the recipient of the sharing request responded. This is a property of a sharing message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingResponseType  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A27  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

The value of this property must be set to one of the following values:
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |No response  <br/> |
|0x00000001  <br/> |Accepted  <br/> |
|0x00000002  <br/> |Denied  <br/> |
   
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

