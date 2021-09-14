---
title: "imapiinitmonitor-wait" 
manager: lindalu
ms.date: 04/27/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIINITMONITOR.Wait
api_type:
- COM
ms.assetid: ed566cae-35a2-4716-817b-54d1ba6825c6
description: IMAPIAMonitor::Wait
Last modified: "April 27, 2021"
---

# IMAPIInitMonitor::Wait
  
**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019
  
Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized. INFINITE can be used to for an infinite wait.

```cpp
HRESULT IMAPIInitMonitor::Wait(DWORD timeout)
```

## Parameters
_timeout_
> [in] The number of milliseconds to wait for MAPI to be initialized, you can pass INFINITE (0xFFFFFFFF) to wait forever.

## Return value

S_OK
> MAPI has been initialized successfully.

HRESULT_FROM_WIN32(ERROR_TIMEOUT)
> When given a non-infinite timeout this indicates MAPI was not initialized during that period.

## See also

[IMAPIInitMonitor](imapiinitmonitoriunknown.md)

[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)

[IMAPIWaitResult](imapiwaitresultiunknown.md)
