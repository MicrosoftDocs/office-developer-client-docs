---
title: "PidTagDisplayNamePrefix Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDisplayNamePrefix
api_type:
- HeaderDef
ms.assetid: 014ce1aa-30b9-4106-82a1-447c370853cf
description: "Last modified: March 09, 2015"
---

# PidTagDisplayNamePrefix Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the display name prefix (such as Miss, Mr., Mrs.) for the messaging user. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DISPLAY_NAME_PREFIX, PR_DISPLAY_NAME_PREFIX_A, PR_DISPLAY_NAME_PREFIX_W  <br/> |
|Identifier:  <br/> |0x3A45  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI mail user  <br/> |
   
## Remarks

These properties provide identification and access information about a messaging user. The content is defined by the messaging user and the messaging user's organization.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
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

