---
title: "imapiinitmonitor-isinitialized" 
manager: lindalu
ms.date: 04/26/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIINITMONITOR.IsInitialized
api_type:
- COM
ms.assetid: 1af0bf93-6bcb-4235-ac30-0d00245ec636
description: IMAPIInitMonitor::IsInitialized
Last modified: "April 26, 2021"
---

# IMAPIINITMONITOR::IsInitialized
  
**Applies to**: Outlook 2013 | Outlook 2016 | 2019
  
Queries MAPI to determine if it currently initialized in the calling process.

```cpp
BOOL IMAPIInitMonitor::IsInitialized()  
```

## Parameters
None

## Return value
A BOOL indicating the current state of MAPI initialization, a value of TRUE means MAPI has been initialized and is available for use, while a value of FALSE means MAPI is currenty uninitialized and is not ready be consumed.

## Remarks
This can be used to determine if MAPI is ready to be used, for example, if your application wanted to do something only if MAPI has already be initialized, this could be a useful check in a background task to prevent the cost of spinning up MAPI for optional work.

## See also

[IMAPIInitMonitor::Wait](imapiinitmonitor-wait.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)
