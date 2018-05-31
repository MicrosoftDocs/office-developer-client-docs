---
title: "IMAPISync  SynchronizeInBackground"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISync.SynchronizeInBackground
api_type:
- COM
ms.assetid: c4aaca65-d553-476c-8c6d-5f880b6efdc1
description: "Last modified: June 26, 2012"
---

# IMAPISync : SynchronizeInBackground

 
  
**Applies to**: Outlook 
  
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

