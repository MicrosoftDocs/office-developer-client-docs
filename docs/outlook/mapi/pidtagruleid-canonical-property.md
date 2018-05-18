---
title: "PidTagRuleId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRuleId
api_type:
- COM
ms.assetid: 341e8db0-52b7-4ba7-aaa6-eedf2783b4e8
description: "Last modified: March 09, 2015"
---

# PidTagRuleId Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies a unique identifier the messaging server generates for each rule when the rule is first created. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RULE_ID  <br/> |
|Identifier:  <br/> |0x6674  <br/> |
|Data type:  <br/> |PT_I8  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

The client must not specify this property when creating a new rule but must specify it when modifying or deleting a rule.
  
When deleting a rule, the only property the client must pass is **PR_RULE_ID** and should not pass in any other property. The server must ignore properties other than this property. When adding a rule, the client must not pass in **PR_RULE_ID**, it must pass in the **PR_RULE_CONDITION** ([PidTagRuleCondition](pidtagrulecondition-canonical-property.md)), **PR_RULE_ACTIONS** ([PidTagRuleActions](pidtagruleactions-canonical-property.md)) and **PR_RULE_PROVIDER** ([PidTagRuleProvider](pidtagruleprovider-canonical-property.md)) properties. When modifying a rule, the client must pass in **PR_RULE_ID** and should pass in the rest of the properties that need to be modified. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx)
  
> Manipulates incoming e-mail messages on a server.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagRuleCondition Canonical Property](pidtagrulecondition-canonical-property.md)
  
[PidTagRuleActions Canonical Property](pidtagruleactions-canonical-property.md)
  
[PidTagRuleProvider Canonical Property](pidtagruleprovider-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

