---
title: "PidTagRuleState Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRuleState
api_type:
- COM
ms.assetid: f62f3055-b855-4203-aa5c-6ba28b58c6f7
description: "Last modified: March 09, 2015"
---

# PidTagRuleState Canonical Property

  
  
**Applies to**: Outlook 
  
A value interpreted as a bitmask combination of flags that specify the state of the rule.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RULE_STATE  <br/> |
|Identifier:  <br/> |0x6677  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

The following table defines the possible values of this property.
  
EN (ST_ENABLED, bitmask 0x00000001)
  
> The rule is enabled for execution. If this flag is not set, the server must skip this rule when evaluating rules.
    
ER (ST_ERROR, bitmask 0x00000002)
  
> The server has encountered an error processing the rule.
    
OF (ST_ONLY_WHEN_OOF, bitmask 0x00000004)
  
> The rule is executed only when the user sets the Out of Office (OOF) state on the mailbox. This flag must not be set in a public folder rule.
    
HI (ST_KEEP_OOF_HIST, bitmask 0x00000008)
  
> This flag must not be set in a public folder rule.
    
EL (ST_EXIT_LEVEL, bitmask 0x00000010)
  
> Rule evaluation will end after executing this rule, except for evaluation of Out of Office rules.
    
SCL (ST_SKIP_IF_SCL_IS_SAFE, bitmask 0x00000020)
  
> Evaluation of this rule may be skipped.
    
PE (ST_RULE_PARSE_ERROR, bitmask 0x00000040)
  
> The server has encountered an error parsing the rule data provided by the client.
    
X
  
> Unused by this protocol. This bit must not be modified by the client.
    
Note on the interaction between ST_ONLY_WHEN_OOF and ST_EXIT_LEVEL flags: 
  
When the "Out of Office" state is set on the mailbox, and a rule condition evaluates to TRUE, 
  
AND:
  
- The rule has the ST_EXIT_LEVEL flag set and does not have ST_ONLY_WHEN_OOF flag set. Then, the server must not evaluate subsequent rules that do not have ST_ONLY_WHEN_OOF flag set, and must evaluate subsequent rules that have ST_ONLY_WHEN_OOF flag set.
    
OR:
  
- The rule has both the ST_EXIT_LEVEL and ST_ONLY_WHEN_OOF flags set. Then, the server must not evaluate any subsequent rules.
    
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

