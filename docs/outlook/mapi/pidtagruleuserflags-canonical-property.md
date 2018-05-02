---
title: "PidTagRuleUserFlags Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRuleUserFlags
api_type:
- COM
ms.assetid: c5dfb21f-b35e-4521-bf2b-e3d03d98d75d
description: "Last modified: March 09, 2015"
---

# PidTagRuleUserFlags Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
This property is set by the client for the exclusive use of the client. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RULE_USER_FLAGS  <br/> |
|Identifier:  <br/> |0x6678  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

The server must preserve the value of this property if it was set by the client. The server must ignore it during rule evaluation and processing.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx)
  
> Manipulates incoming e-mail messages on a server.
    
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

