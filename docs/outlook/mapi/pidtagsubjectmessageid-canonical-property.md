---
title: "PidTagSubjectMessageId Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagSubjectMessageId
api_type:
- COM
ms.assetid: d4b1a087-0986-467a-aaa9-fc643f7c56fc
description: "Contains a binary value that is copied from the message for which a report is being generated. This property can correlate a report with the original message."
---

# PidTagSubjectMessageId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a binary value that is copied from the message for which a report is being generated. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_SUBJECT_IPM  <br/> |
|Identifier:  <br/> |0x0038  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property, like the **PR_REPORT_TAG** ([PidTagReportTag](pidtagreporttag-canonical-property.md)) property, can be used to correlate a report with the original message. 
  
## Related resources

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

