---
title: "imapiinitmonitor-beginwait" 
manager: lindalu
ms.date: 03/30/2021
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
Last modified: "March 30, 2021"
---

# IMAPIINITMONITOR::BeginWait
  
**Applies to**: Outlook 2013 | Outlook 2016 | 2019
  
IFACEMETHODIMP BeginWait(DWORD timeout, IMAPIWaitResult** ppResult)
Start a wait for MAPI initialization or the specified number of milliseconds to elapse. This returns an IMAPIWaitResult interface which should have **End** called in order begin the wait. This allows the caller to control which thread is blocked while we are waiting.

## Parameters

## Return value

## Remarks
  
## See also

[IPSTOVERRIDEREQ::IsInitialized](imapiinitmonitor-isinitialized.md)

[IMAPIInitMonitor::Wait](imapiinitmonitor-wait.md)
