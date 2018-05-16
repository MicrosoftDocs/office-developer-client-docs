---
title: "MAPIUninitialize"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPIUninitialize
api_type:
- HeaderDef
ms.assetid: 0f4e54dc-80e5-49a7-9703-0225d8133492
description: "Last modified: March 09, 2015"
---

# MAPIUninitialize

  
  
**Applies to**: Outlook 
  
Decrements the reference count, cleans up, and deletes per-instance global data for the MAPI DLL. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
void MAPIUninitialize ( void );
```

## Parameters

None 
  
## Return value

None.
  
## Remarks

A client application calls the **MAPIUninitialize** function to end its interaction with MAPI, begun with a call to the [MAPIInitialize](mapiinitialize.md) function. After **MAPIUninitialize** is called, no other MAPI calls can be made by the client. 
  
 **MAPIUninitialize** decrements the reference count, and the corresponding **MAPIInitialize** function increments the reference count. Thus, the number of calls to one function must equal the number of calls to the other. 
  
> [!NOTE]
> You cannot call **MAPIInitialize** or **MAPIUninitialize** from within a Win32 **DllMain** function or any other function that creates or terminates threads. For more information, see [Using Thread-Safe Objects](using-thread-safe-objects.md). 
  

