---
title: "IMAPIWaitResult::End" 
manager: lindalu
ms.date: 04/26/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIWaitResult.End
api_type:
- COM
ms.assetid: 7463c9e8-d065-4cc3-ac01-d428b57bbc88
description: IMAPIWaitResult::End
Last modified: "April 26, 2021"
---

# IMAPIWaitResult::End
  
**Applies to**: Outlook 2013 | Outlook 2016 | 2019

Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized.  INFINITE can be used to for an infinite wait.

```cpp
HRESULT IMAPIWaitResult::End(DWORD timeout)
```

## Parameters

_timeout_
> [in] The number of millisecond to wait for MAPI to be initialized, you can pass INFINITE to wait forever.

## Return value

S_OK
> MAPI has been initialized successfully

HRESULT_FROM_WIN32(ERROR_TIMEOUT)
> When given a non-infinite timeout this indicates MAPI was not initialized during that period.

## Remarks
This API behaves exactly the same as [IMAPInitMonitor::Wait](imapiinitmonitor-wait.md)
  
## See also

[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)

[IMAPIWaitResult](imapiwaitresultiunknown.md)
