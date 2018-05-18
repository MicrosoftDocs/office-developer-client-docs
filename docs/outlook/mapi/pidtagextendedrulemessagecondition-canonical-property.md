---
title: "PidTagExtendedRuleMessageCondition Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExtendedRuleMessageCondition
api_type:
- HeaderDef
ms.assetid: 891851e1-e4a4-4c20-a26c-7223bcca35f7
description: "Last modified: March 09, 2015"
---

# PidTagExtendedRuleMessageCondition Canonical Property

  
  
**Applies to**: Outlook 
  
Contains information about any named properties that are contained inside of extended rule conditions.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXTENDED_RULE_MSG_CONDITION  <br/> |
|Identifier:  <br/> |0x0E9A  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Rules  <br/> |
   
## Remarks

This property must be set on an FAI message. It serves the same purpose as **PR_RULE_CONDITION** ([PidTagRuleCondition](pidtagrulecondition-canonical-property.md)), but contains additional information about the named properties used. All string values contained in any part of this condition property value must be in Unicode format.
  
For information about the format of this binary property, see [[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx).
  
## Related resources

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



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

