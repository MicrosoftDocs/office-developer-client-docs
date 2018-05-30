---
title: "PidTagRuleActions Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRuleActions
api_type:
- COM
ms.assetid: 3ec4259a-8fe9-46c3-82b8-42c6907b8515
description: "Last modified: March 09, 2015"
---

# PidTagRuleActions Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the set of actions associated with the rule. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RULE_ACTIONS  <br/> |
|Identifier:  <br/> |0x6680  <br/> |
|Data type:  <br/> |PT_ACTIONS  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

The actions are expressed as a rule action and the property value buffer contains the rule action data buffer structure packaged as specified in [[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ImportProcs.cpp  <br/> |PropCopyMore, HrCopyActions  <br/> |These functions demonstrate how to parse a PT_ACTIONS property for the purposes of copying to another property.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXORULE]](http://msdn.microsoft.com/library/70ac9436-501e-43e2-9163-20d2b546b886%28Office.15%29.aspx)
  
> Manipulates incoming email messages on a server.
    
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

