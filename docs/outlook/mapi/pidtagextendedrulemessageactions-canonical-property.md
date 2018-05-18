---
title: "PidTagExtendedRuleMessageActions Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagExtendedRuleMessageActions
api_type:
- HeaderDef
ms.assetid: 1cf277d4-76ec-4902-9e54-f1780cee49bf
description: "Last modified: March 09, 2015"
---

# PidTagExtendedRuleMessageActions Canonical Property

  
  
**Applies to**: Outlook 
  
Contains additional information about the named properties used in a Folder Associated Information (FAI) message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EXTENDED_RULE_MSG_ACTIONS  <br/> |
|Identifier:  <br/> |0x0E99  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Rules  <br/> |
   
## Remarks

This property must be set on an FAI message. This property serves the same purpose as **PR_RULE_ACTIONS** ([PidTagRuleActions](pidtagruleactions-canonical-property.md)), but contains additional information about the version of the rule and the named properties stored in the rule action, as well as information about the actions to be performed by this rule. All string values contained in any part of the action buffer used to contain actions must be in Unicode format.
  
For information about the format of this binary property, see [[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx).
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications..
    
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

