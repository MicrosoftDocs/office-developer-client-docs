---
title: "PidTagReportDispositionMode Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 67b3c76a-f6f7-462b-955c-dc7b53e7e7eb
description: "Indicates the disposition of the receipt for messages that request receipts for Outlook 2013 or Outlook 2016."
---

# PidTagReportDispositionMode Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the disposition of the receipt for messages that request receipts. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_REPORT_DISPOSITION_MODE, PR_REPORT_DISPOSITION_MODE_A, PR_REPORT_DISPOSITION_MODE_W  <br/> |
|Identifier:  <br/> |0x0081  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

The possible values for this property are "manual-action/MDN-sent-automatically" and "manual-action/MDN-sent-manually".
  
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

