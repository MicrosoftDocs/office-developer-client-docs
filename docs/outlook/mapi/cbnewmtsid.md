---
title: "CbNewMTSID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CbNewMTSID
api_type:
- COM
ms.assetid: fd5ef226-39e6-4604-a751-2f6cc49c4895
description: "Last modified: March 09, 2015"
---

# CbNewMTSID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Computes the number of bytes that should be allocated for a new [MTSID](mtsid.md) structure with a message transfer agent identifier of a specified size. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**MTSID** <br/> |
   
```cpp
CbNewMTSID (_cb)
```

## Parameters

 __cb_
  
> Count of bytes for the message transfer agent identifier to be included in the new **MTSID** structure. 
    
## See also



[MTSID](mtsid.md)


[Macros Related to Structures](macros-related-to-structures.md)

