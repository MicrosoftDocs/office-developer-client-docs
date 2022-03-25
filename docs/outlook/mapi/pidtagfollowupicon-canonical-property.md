---
title: "PidTagFollowupIcon Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFollowupIcon
api_type:
- HeaderDef
ms.assetid: 374cef41-141a-491b-8dd1-eaf1a2044204
description: "Last modified: March 09, 2015"
---

# PidTagFollowupIcon Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the flag color of the message object.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_FOLLOWUP_ICON  <br/> |
|Identifier:  <br/> |0x1095  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Rename message folder  <br/> |
   
## Remarks

This property must not exist unless the value of the **PR_FLAG_STATUS** ([PidTagFlagStatus](pidtagflagstatus-canonical-property.md)) property is set to "followupFlagged", or the message object is a meeting-related object. This property should not exist on a task object. When set on other message objects, this property must be set to one of the following values.
  
|**Numeric value**|**Name**|**Description**|
|:-----|:-----|:-----|
|Not present  <br/> |N/A  <br/> |No color  <br/> |
|1  <br/> |followupIcon1  <br/> |Purple flag  <br/> |
|2  <br/> |followupIcon2  <br/> |Orange flag  <br/> |
|3  <br/> |followupIcon3  <br/> |Green flag  <br/> |
|4  <br/> |followupIcon4  <br/> |Yellow flag  <br/> |
|5  <br/> |followupIcon5  <br/> |Blue flag  <br/> |
|6  <br/> |followupIcon6  <br/> |Red flag  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOFLAG]](https://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
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

