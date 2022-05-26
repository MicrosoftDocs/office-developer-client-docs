---
title: "PidTagLastVerbExecuted Canonical Property"
description: Outlines the PidTagLastVerbExecuted canonical property, which contains the last verb executed. There are also links to reference materials.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagLastVerbExecuted
api_type:
- HeaderDef
ms.assetid: 502f0261-697f-41bf-8530-75e1d0f503e5
---

# PidTagLastVerbExecuted Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the last verb executed.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_LAST_VERB_EXECUTED  <br/> |
|Identifier:  <br/> |0x1081  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |History  <br/> |
   
## Remarks

This property can have one the following values:
  
|**Verb**|**Property value**|
|:-----|:-----|
|Post  <br/> |0x00000001  <br/> |
|Other  <br/> |0x00000003  <br/> |
|Read mail  <br/> |0x00000100  <br/> |
|Unread mail  <br/> |0x00000101  <br/> |
|Submitted mail  <br/> |0x00000102  <br/> |
|Unsent mail  <br/> |0x00000103  <br/> |
|Receipt mail  <br/> |0x00000104  <br/> |
|Replied mail  <br/> |0x00000105  <br/> |
|Forwarded mail  <br/> |0x00000106  <br/> |
|Remote mail  <br/> |0x00000107  <br/> |
|Delivery Receipt  <br/> |0x00000108  <br/> |
|Read Receipt  <br/> |0x00000109  <br/> |
|Nondelivery Receipt  <br/> |0x0000010A  <br/> |
|Nonread Receipt  <br/> |0x0000010B  <br/> |
|Recall_S mail  <br/> |0x0000010C  <br/> |
|Recall_F mail  <br/> |0x0000010D  <br/> |
|Tracking mail  <br/> |0x0000010E  <br/> |
|Out of Office mail  <br/> |0x0000011B  <br/> |
|Recall mail  <br/> |0x0000011C  <br/> |
|Tracked mail  <br/> |0x00000139  <br/> |
|Contact  <br/> |0x00000200  <br/> |
|Distribution List  <br/> |0x00000201  <br/> |
|Sticky Note, Blue  <br/> |0x00000300  <br/> |
|Sticky Note, Green  <br/> |0x00000301  <br/> |
|Sticky Note, Pink  <br/> |0x00000302  <br/> |
|Sticky Note, Yellow  <br/> |0x00000303  <br/> |
|Sticky Note, White  <br/> |0x00000304  <br/> |
|Single Instance Appointment  <br/> |0x00000400  <br/> |
|Recurring Appointment  <br/> |0x00000401  <br/> |
|Single Instance Meeting  <br/> |0x00000402  <br/> |
|Recurring Meeting  <br/> |0x00000403  <br/> |
|Meeting Request / Full Update  <br/> |0x00000404  <br/> |
|Accept  <br/> |0x00000405  <br/> |
|Decline  <br/> |0x00000406  <br/> |
|Tentatively Accept  <br/> |0x00000407  <br/> |
|Cancelation  <br/> |0x00000408  <br/> |
|Informational Update  <br/> |0x00000409  <br/> |
|Task/Task Update  <br/> |0x00000500  <br/> |
|Unassigned Recurring Task  <br/> |0x00000501  <br/> |
|Assignee's Task  <br/> |0x00000502  <br/> |
|Assigner's Task  <br/> |0x00000503  <br/> |
|Task Request  <br/> |0x00000504  <br/> |
|Task Acceptance  <br/> |0x00000505  <br/> |
|Task Rejection  <br/> |0x00000506  <br/> |
|Journal Conversation  <br/> |0x00000601  <br/> |
|Journal Email Message  <br/> |0x00000602  <br/> |
|Journal Meeting request  <br/> |0x00000603  <br/> |
|Journal Meeting response  <br/> |0x00000604  <br/> |
|Journal Task request  <br/> |0x00000606  <br/> |
|Journal Task response  <br/> |0x00000607  <br/> |
|Journal Note  <br/> |0x00000608  <br/> |
|Journal Fax  <br/> |0x00000609  <br/> |
|Journal Phone call  <br/> |0x0000060A  <br/> |
|Journal Task  <br/> |0x0000060B  <br/> |
|Journal Letter  <br/> |0x0000060C  <br/> |
|Journal Microsoft Office Word  <br/> |0x0000060D  <br/> |
|Journal Microsoft Office Excel  <br/> |0x0000060E  <br/> |
|Journal Microsoft Office PowerPoint  <br/> |0x0000060F  <br/> |
|Journal Microsoft Office Access  <br/> |0x00000610  <br/> |
|Journal Document  <br/> |0x00000612  <br/> |
|Journal Meeting  <br/> |0x00000613  <br/> |
|Journal Meeting cancellation  <br/> |0x00000614  <br/> |
|Journal Remote session  <br/> |0x00000615  <br/> |
|New mail  <br/> |0xFFFFFFFF  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCICAL]](https://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> 
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

