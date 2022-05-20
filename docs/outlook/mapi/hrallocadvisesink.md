---
title: "HrAllocAdviseSink"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- HrAllocAdviseSink
api_type:
- HeaderDef
ms.assetid: 1dd460e6-ce95-4fef-bb5e-8d778c9716d5
description: "Last modified: March 09, 2015"
---

# HrAllocAdviseSink

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates an advise sink object, given a context specified by the calling implementation and a callback function to be triggered by an event notification. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
STDAPI HrAllocAdviseSink(
  LPNOTIFCALLBACK lpfnCallback,
  LPVOID lpvContext,
  LPMAPIADVISESINK FAR * lppAdviseSink
);
```

## Parameters

 _lpfnCallback_
  
> [in] Pointer to a callback function based on the [NOTIFCALLBACK](notifcallback.md) prototype that MAPI is to call when a notification event occurs for the newly created advise sink. 
    
 _lpvContext_
  
> [in] Pointer to caller data passed to the callback function when MAPI calls it. The caller data can represent an address of significance to the client or provider. Typically, for C++ code, the  _lpvContext_ parameter represents a pointer to the address of an object. 
    
 _lppAdviseSink_
  
> [out] Pointer to a pointer to an advise sink object.
    
## Return value

None.
  
## Remarks

To use the **HrAllocAdviseSink** function, a client application or service provider creates an object to receive notifications, creates a notification callback function based on the [NOTIFCALLBACK](notifcallback.md) function prototype that goes with that object, and passes a pointer to the object in the **HrAllocAdviseSink** function as the  _lpvContext_ value. Doing so performs a notification; and as part of the notification process, MAPI calls the callback function with the object pointer as the context. 
  
MAPI implements its notification engine asynchronously. In C++, the notification callback can be an object method. If the object generating the notification is not present, the client or provider requesting notification must keep a separate reference count for that object for the object's advise sink. 
  
> [!CAUTION]
> **HrAllocAdviseSink** should be used sparingly; it is safer for clients to create their own advise sinks. 
  

