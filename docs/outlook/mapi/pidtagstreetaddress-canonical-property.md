---
title: "PidTagStreetAddress Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagStreetAddress
api_type:
- COM
ms.assetid: 41262e7a-5f5f-4830-b80c-f1be3e9a3276
description: "Last modified: March 09, 2015"
---

# PidTagStreetAddress Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the recipient's street address. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_STREET_ADDRESS, PR_STREET_ADDRESS_A, PR_STREET_ADDRESS_W, PR_BUSINESS_ADDRESS_STREET, PR_BUSINESS_ADDRESS_STREET_A, PR_BUSINESS_ADDRESS_STREET_W  <br/> |
|Identifier:  <br/> |0x3A29  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI mail user  <br/> |
   
## Remarks

These properties provide identification and access information for a recipient. They are defined by the recipient and the recipient's organization. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

