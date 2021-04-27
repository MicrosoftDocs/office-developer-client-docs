---
title: "imapiinitmonitor-beginwait" 
manager: lindalu
ms.date: 04/27/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIINITMONITOR.BeginWait
api_type:
- COM
ms.assetid: 71f565a9-651c-42b5-9102-91b728b681ae
description: IMAPIInitMonitor::BeginWait"
Last modified: "April 27, 2021"
---

# IMAPIInitMonitor::BeginWait
  
**Applies to**: Outlook 2016 | Outlook 2019
  
Start a wait for MAPI initialization or the specified number of milliseconds to elapse. This returns an IMAPIWaitResult interface which should have **IMAPIWaitResult::End** called in order initiate the wait. This allows the caller to control which thread is blocked while we are waiting.

```cpp
HRESULT IMAPIInitMonitor::BeginWait(DWORD timeout, IMAPIWaitResult** ppResult)
```

## Parameters
_timeout_
>[in] The number of millisecond to wait for MAPI initialization, this can set to INFINITE to wait forever for the initialization to happen.

_ppResult_
>[out] A pointer to recieve the newly create wait interface.

## Return value
S_OK
>A wait operation was successfully started.

E_OUTOFMEMORY
>There was not enough memory to create a new object.

## Remarks
This API provided the caller with an interface (which is thread-safe) which can be used initiate a blocking wait for MAPI initialization. This allows the consumer to deterime the best wait to wait for thier application. The behavior of calling IMAPIWaitResult::End is identical to calling IMAPIInitMonitor::Wait.

## See also

[IMAPIInitMonitor](imapiinitmonitoriunknown.md)

[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::Wait](imapiinitmonitor-wait.md)

[IMAPIWaitResult](imapiwaitresultiunknown.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)
