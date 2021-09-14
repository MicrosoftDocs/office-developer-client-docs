---
title: "UlRelease"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.UlRelease
api_type:
- COM
ms.assetid: 95db96ef-f95f-41da-b216-f717c23bffd2
description: "Last modified: March 09, 2015"
---

# UlRelease

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides an alternative way to invoke the OLE method **IUnknown::Release**. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
ULONG UlRelease(
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

The reference count is the number of existing pointers to the object to be released. 
  
If the  _punk_ parameter is NULL, the function returns immediately without calling **IUnknown::Release**
  
 **UlRelease** returns the value returned by the **IUnknown::Release** method, which can be equal to the reference count for the object to be released. 
  
For more information about **IUnknown::Release**, see [Implementing the IUnknown Interface](implementing-the-iunknown-interface.md). 
  

