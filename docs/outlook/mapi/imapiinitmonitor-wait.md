---
title: "imapiinitmonitor-wait" 
manager: lindalu
ms.date: 03/30/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIINITMONITOR.Wait
api_type:
- COM
ms.assetid: ed566cae-35a2-4716-817b-54d1ba6825c6
description: 
Last modified: March 30, 2021
---

# IMAPIINITMONITOR::Wait
  
**Applies to**: Outlook 2013 | Outlook 2016 | 2019
  
IFACEMETHODIMP Wait(DWORD timeout)
Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized.  INFINITE can be used to for an infinite wait.

## Parameters

## Return value

## Remarks
  
## See also

[IPSTOVERRIDEREQ::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md)
