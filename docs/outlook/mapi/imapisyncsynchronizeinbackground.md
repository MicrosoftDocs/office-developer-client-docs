---
title: "IMAPISync  SynchronizeInBackground"
description: "IMAPISync SynchronizeInBackground initiates a synchronization. It is called by Microsoft Outlook 2010 and 2013 and implemented by message store providers."
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISync.SynchronizeInBackground
api_type:
- COM
ms.assetid: c4aaca65-d553-476c-8c6d-5f880b6efdc1
---

# IMAPISync : SynchronizeInBackground

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 Initiates a synchronization. This method is called by Microsoft Outlook 2010 and Microsoft Outlook 2013 and implemented by message store providers. 
  
```cpp
HRESULT SynchronizeInBackground (
  PMAPISIB psibpb
);
```

## Parameters

 _psibpb_
  
> Informs the provider of what will be synchronized and gives access to interfaces that can be used during the synchronization. It is a [MAPISIB](mapisib.md) structure. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## See also



[IMAPISync : IUnknown](imapisynciunknown.md)
  
[MAPISIB](mapisib.md)

