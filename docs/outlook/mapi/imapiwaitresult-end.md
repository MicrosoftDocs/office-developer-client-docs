---
title: "IMAPIWaitResult::End" 
manager: lindalu
ms.date: 04/27/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIWaitResult.End
api_type:
- COM
ms.assetid: 7463c9e8-d065-4cc3-ac01-d428b57bbc88
description: IMAPIWaitResult::End
Last modified: "April 27, 2021"
---

# IMAPIWaitResult::End
  
**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019

Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized. INFINITE can be used to for an infinite wait.

```cpp
HRESULT IMAPIWaitResult::End(DWORD timeout)
```

## Parameters

_timeout_
> [in] The number of millisecond to wait for MAPI to be initialized, you can pass INFINITE (0xFFFFFFFF) to wait forever.

## Return value

S_OK
> MAPI has been initialized successfully

HRESULT_FROM_WIN32(ERROR_TIMEOUT)
> When given a non-infinite timeout this indicates MAPI was not initialized during that period.

## Remarks
This API behaves exactly the same as [IMAPInitMonitor::Wait](imapiinitmonitor-wait.md).
  
## See also

[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md)

[IMAPIWaitResult](imapiwaitresultiunknown.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)
