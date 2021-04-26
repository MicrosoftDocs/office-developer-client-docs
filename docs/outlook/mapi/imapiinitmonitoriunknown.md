---
title: "IMAPIInitMoniter : IUnknown"  
manager: lindalu
26ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIInitMoniter
api_type:
- COM
ms.assetid: ad71ea65-394d-4be2-a9da-cd23099bc2cc
description: IMAPIInitMonitor
Last modified: "April 26, 2021"
---

# IMAPIInitMonitor : IUnknown

**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019

This interface used by consumers of IMAPIInitMonitor to control where the wait happens, it allows them create the object on one thread move it another thread to perform the actual wait.

## Vtable order

| function | description |
|:-----|:-----|
|[HRESULT IMAPIWaitResult::End()](imapiwaitresult-end.md)|Called to initiate the blocking wait on the thread where it is called, does not need to be the same thread that called *IMAPIInitMonitor::BeginWait*.|

| quick info | result |
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> |  OLMAPI32.DLL<br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIWaitResult  <br/> |

## See also

[IMAPIInitMonitor](imapiinitmonitoriunknown.md)

[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md)

[IMAPIInitMonitor : IUnknown](imapiinitmonitoriunknown.md)

[CreateMAPIInitializationMonitor](createmapiinitializationmonitor.md)
