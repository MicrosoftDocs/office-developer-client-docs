---
title: "MAPIINIT_0"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MAPIINIT_0
api_type:
- COM
ms.assetid: 70739711-ff43-407d-bc8b-6baf7a476fef
description: "Last modified: March 09, 2015"
---

# MAPIINIT_0

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Conveys options to the [MAPIInitialize](mapiinitialize.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |MAPIX.H  <br/> |
   
```cpp
typedef struct
{
  ULONG ulVersion;
  ULONG ulFlags;
} MAPIINIT_0, FAR *LPMAPIINIT_0;

```

## Members

 **ulVersion**
  
> An integer value that represents the version number of the **MAPIINIT_0** structure. The **ulVersion** member is for future expansion and does not represent the version of the MAPI interface. Currently, **ulVersion** must be set to MAPI_INIT_VERSION. 
    
 **ulFlags**
  
> The bitmask of flags used to control the initialization of the MAPI session. The following flags can be set:
    
MAPI_MULTITHREAD_NOTIFICATIONS 
  
> MAPI should generate notifications using a thread dedicated to notification handling instead of the first thread used to call **MAPIInitialize**.
    
MAPI_NT_SERVICE 
  
> The caller is running as a Windows service. Callers that are not running as a Windows service should not set this flag; callers that are running as a service must set this flag.
    
MAPI_NO_COINIT
  
> Set the MAPI_NO_COINT flag so that **MAPIInitialize** does not try to initialize COM with a call to [CoInitialize](http://msdn.microsoft.com/library/0f171cf4-87b9-43a6-97f2-80ed344fe376%28Office.15%29.aspx). If a **MAPIINIT_0** structure is passed into **MAPIInitialize** with  _ulFlags_ set to MAPI_NO_COINIT, MAPI will assume that COM has already been initialized and will bypass the call to **CoInitialize**.
    
## Remarks

Multithreaded clients should set the MAPI_MULTITHREAD_NOTIFICATIONS flag. If the flag is not set, notifications are generated on the thread used to make the first call to **MAPIInitialize**. 
  
For more information about when to set this flag and how to implement thread safety in a client, see [Threading in MAPI](threading-in-mapi.md). 
  
## See also



[MAPIInitialize](mapiinitialize.md)


[MAPI Structures](mapi-structures.md)

