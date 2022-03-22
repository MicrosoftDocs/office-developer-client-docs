---
title: "PidTagReportDisposition Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 56b9e7bd-eece-4264-8ee5-a1bcbec4f35c
description: "Indicates the receipt status for messages that request receipts."
---

# PidTagReportDisposition Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the receipt status for messages that request receipts. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_REPORT_DISPOSITION, PR_REPORT_DISPOSITION_A, PR_REPORT_DISPOSITION_W  <br/> |
|Identifier:  <br/> |0x0080  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

The following are valid values:
  
- "deleted"
    
- "processed"
    
- "dispatched"
    
- "denied"
    
- "failed"
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]] 
  
> Provides references to related Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

