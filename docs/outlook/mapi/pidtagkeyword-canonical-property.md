---
title: "PidTagKeyword Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagKeyword
api_type:
- HeaderDef
ms.assetid: 8dbfb22d-93db-468c-b2a4-eaa2b545bd61
description: "Last modified: March 09, 2015"
---

# PidTagKeyword Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a keyword that identifies the recipient to the recipient's system administrator.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_KEYWORD, PR_KEYWORD_A, PR_KEYWORD_W  <br/> |
|Identifier:  <br/> |0x3A0B  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

These properties provide identification and access information for a recipient. They are defined by the recipient and their organization.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

