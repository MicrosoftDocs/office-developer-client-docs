---
title: "PidTagLocation Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagLocation
api_type:
- HeaderDef
ms.assetid: 99dffcd9-83dc-462e-b0ce-e2101e546cc6
description: "Contains the location of the recipient in a format that is useful to the recipient's organization. These properties are defined by the recipient and their organization."
---

# PidTagLocation Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the location of the recipient in a format that is useful to the recipient's organization. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_LOCATION, PR_LOCATION_A, PR_LOCATION_W  <br/> |
|Identifier:  <br/> |0x3A0D  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

These properties provide identification and access information for a recipient. They are defined by the recipient and their organization. 
  
The contents are defined by the needs of the recipient's organization. For example, some organizations might identify messaging users by specifying the building number and office number. 
  
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
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

