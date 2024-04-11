---
title: "PidTagOriginalSubmitTime Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginalSubmitTime
api_type:
- COM
ms.assetid: 2e027c0c-2370-437a-ad98-2bbb5e41e525
description: "Contains the original submission date and time of the message in the report. It is not changed when the message is forwarded."
---

# PidTagOriginalSubmitTime Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the original submission date and time of the message in the report.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_SUBMIT_TIME  <br/> |
|Identifier:  <br/> |0x004E  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

At first submission of a message, a client application should set this property to the value of the **PR_CLIENT_SUBMIT_TIME** ([PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md)) property. It is not changed when the message is forwarded. This is used in reports only.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on email message objects.
    
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

