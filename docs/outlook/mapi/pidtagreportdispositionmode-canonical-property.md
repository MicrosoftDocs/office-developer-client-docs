---
title: "PidTagReportDispositionMode Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_type:
- COM
ms.assetid: 67b3c76a-f6f7-462b-955c-dc7b53e7e7eb
description: "Last modified: March 09, 2015"
---

# PidTagReportDispositionMode Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Indicates the disposition of the receipt for messages that request receipts. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_REPORT_DISPOSITION_MODE, PR_REPORT_DISPOSITION_MODE_A, PR_REPORT_DISPOSITION_MODE_W  <br/> |
|Identifier:  <br/> |0x0081  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

The possible values for this property are "manual-action/MDN-sent-automatically" and "manual-action/MDN-sent-manually".
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](f6ab1613-aefe-447d-a49c-18217230b148)
  
> Provides references to related Exchange Server protocol specifications.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

