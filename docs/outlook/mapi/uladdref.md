---
title: "UlAddRef"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.UlAddRef
api_type:
- COM
ms.assetid: 9b897cbc-90b2-4c60-b5f1-dc78e7e7952d
description: "Last modified: March 09, 2015"
---

# UlAddRef

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides an alternative way to invoke the OLE method **IUnknown::AddRef**. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
ULONG UlAddRef(
  LPVOID punk
);
```

## Parameters

 _punk_
  
> [in] Pointer to an interface derived from the **IUnknown** interface, in other words any MAPI interface. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_CALL_FAILED 
  
> An error of unexpected or unknown origin prevented the operation from completing.
    
## Remarks

 **UlAddRef** returns the value returned by the **IUnknown::AddRef** method, which is the new value of the reference count for the interface. The value is nonzero. 
  
For more information about **IUnknown::AddRef**, see [Implementing the IUnknown Interface](implementing-the-iunknown-interface.md). 
  

