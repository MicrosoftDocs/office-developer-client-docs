---
title: "PidTagExtendedRuleSizeLimit Canonical Property"
description: Outlines the PidTagExtendedRuleSizeLimit canonical property, which contains the maximum size the user is allowed to accumulate for a single "extended" rule.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagExtendedRuleSizeLimit
api_type:
- HeaderDef
ms.assetid: 87186764-fb58-4cdf-804d-bb13c5a8cb65
---

# PidTagExtendedRuleSizeLimit Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the maximum size, in bytes, the user is allowed to accumulate for a single "extended" rule.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_EXTENDED_RULE_SIZE_LIMIT  <br/> |
|Identifier:  <br/> |0x0E9B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Rules  <br/> |
   
## Remarks

If this property is set on the logon object, the client should keep the size of the **PR_EXTENDED_RULE_MSG_CONDITION** ([PidTagExtendedRuleMessageCondition](pidtagextendedrulemessagecondition-canonical-property.md)) property under the value specified by this property. Conversely, the server should return an error if the client does attempt to set a binary property that is too large.
  
For information about extended rules, see [[MS-OXORULE]](https://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSTOR]](https://msdn.microsoft.com/library/d42ed1e0-3e77-4264-bd59-7afc583510e2%28Office.15%29.aspx)
  
> Specifies permissible operations for the core message store objects.
    
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

