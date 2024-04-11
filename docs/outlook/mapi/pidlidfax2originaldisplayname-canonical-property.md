---
title: "PidLidFax2OriginalDisplayName Canonical Property"
description: Outlines the PidLidFax2OriginalDisplayName canonical property, which specifies the original display name of the contact's home fax address.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidFax2OriginalDisplayName
api_type:
- COM
ms.assetid: 7f521e27-834c-4fb5-9782-2c5d1380690f
---

# PidLidFax2OriginalDisplayName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the original display name of the contact's home fax address.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidFax2OriginalDisplayName  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x000080C4  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

This property, if present, must be set to the same value as the **PR_NORMALIZED_SUBJECT** ([PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md)) property.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

