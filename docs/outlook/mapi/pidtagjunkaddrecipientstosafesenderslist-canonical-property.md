---
title: "PidTagJunkAddRecipientsToSafeSendersList Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagJunkAddRecipientsToSafeSendersList
api_type:
- HeaderDef
ms.assetid: 78543caa-e6ec-4ac7-bfdd-70c56f8fd955
description: "Last modified: March 09, 2015"
---

# PidTagJunkAddRecipientsToSafeSendersList Canonical Property

  
  
**Applies to**: Outlook 
  
Indicates whether or not the mail recipients are to be added to the safe senders list.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_JUNK_ADD_RECIPS_TO_SSL  <br/> |
|Identifier:  <br/> |0x6103  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Spam  <br/> |
   
## Remarks

If present, this property must be set to 0 or 1. A value of 1 indicates that the mail recipients are to be added to the safe senders list. A value of 0 indicates that the mail recipients are not to be added to the safe senders list.
  
If this property is present with a value of 1, the SMTP addresses of the e-mail recipients must be added to trusted senders clause of the Junk E-Mail Rule condition. If this property is 0, no action is required.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSPAM]](http://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk e-mail messages.
    
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

