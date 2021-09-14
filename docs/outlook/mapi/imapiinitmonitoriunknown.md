---
title: "IMAPIInitMonitor : IUnknown"  
manager: lindalu
26ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIInitMonitor
api_type:
- COM
ms.assetid: ad71ea65-394d-4be2-a9da-cd23099bc2cc
description: IMAPIInitMonitor
Last modified: "April 27, 2021"
---

# IMAPIInitMonitor : IUnknown

**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019

There are times when an application which consumes MAPI might want to know when the initialization is completed. For example, it has multiple threads which could initialize MAPI, or in response to MAPI being initialized the application would like perform some work, but does not want to always spin up the MAPI stack. The initialization monitor provides this functionality through a [CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md) object.

| quick info | result |
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> | OLMAPI32.DLL <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIInitMonitor  <br/> |

## Vtable order

| function | description |
|:-----|:-----|
|[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md) <br/> |Returns the current state of MAPI initialization.  <br/> |
|[IMAPIInitMonitor::Wait](imapiinitmonitor-wait.md) <br/> |Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized.  INFINITE can be used to for an infinite wait.  <br/> |
|[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md) <br/> |Start a wait for MAPI initialization or the specified number of milliseconds to elapse. This return an IMAPIWaitResult interface which should have “End” called in order begin the wait.  This allows the caller to control which thread is blocked while we are waiting. <br/> |

## See also

[IMAPIInitMonitor](imapiinitmonitoriunknown.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)
