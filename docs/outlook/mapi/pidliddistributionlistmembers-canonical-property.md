---
title: "PidLidDistributionListMembers Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidDistributionListMembers
api_type:
- COM
ms.assetid: 029767ab-de72-4402-9cc3-31b006591042
description: "Last modified: March 09, 2015"
---

# PidLidDistributionListMembers Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the list of EntryIds of the objects that correspond to the members of the personal distribution list.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidDLMembers  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008055  <br/> |
|Data type:  <br/> |PT_MV_BINARY  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

Members of the personal distribution list can be other personal distribution lists, electronic addresses contained in a contact, Global Address List users or distribution lists, or one-off email addresses. The format of each EntryId must be either a one-off EntryId, as specified in [[MS-OXCDATA],](https://msdn.microsoft.com/library/1afa0cd9-b1a0-4520-b623-bf15030af5d8%28Office.15%29.aspx) or a wrapped EntryId. 
  
When setting this property, the client or the server must ensure its total size is less than 15,000 bytes.
  
This property specifies the list of one-off EntryIds that correspond to the members of the personal distribution list. These one-off EntryIds encapsulate display names and email addresses of the personal distribution list members.
  
If the client or the server set this property, it must be synchronized with this property **dispidDLMembers** for each entry in the **dispidDLOneOffMembers** ([PidLidDistributionListOneOffMembers](pidliddistributionlistoneoffmembers-canonical-property.md)) property, there must be an entry in the same position in the **dispidDLOneOffMembers**.
  
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

