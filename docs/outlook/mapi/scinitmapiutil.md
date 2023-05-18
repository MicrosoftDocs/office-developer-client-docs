---
title: "ScInitMapiUtil"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ScInitMapiUtil
api_type:
- HeaderDef
ms.assetid: d83b8ea8-a3b8-4038-a226-de1869c5d722
description: "Replaces MAPIInitialize when only select utility functions are being used for Outlook 2013 or Outlook 2016."
---

# ScInitMapiUtil

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Replaces [MAPIInitialize](mapiinitialize.md) when only select utility functions are being used. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
SCODE ScInitMapiUtil(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

The **ScInitMapiUtil** and [DeinitMapiUtil](deinitmapiutil.md) functions cooperate to call and release select utility functions, as opposed to [MAPIInitialize](mapiinitialize.md), which calls core as well as utility functions. When **ScInitMapiUtil** calls utility functions, it also initializes the necessary memory. 
  
When use of the functions that **ScInitMapiUtil** has called is complete, **DeinitMapiUtil** must be explicitly called to release them. In contrast, **MAPIInitialize** implicitly calls **DeinitMapiUtil**. 
  
## See also



[MAPIUninitialize](mapiuninitialize.md)

