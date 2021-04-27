---
title: "IMAPIWaitResult : IUnknown" 
manager: lindalu
ms.date: 04/26/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIWAITRESULT
api_type:
- COM
ms.assetid: d7157f57-709d-4e53-973b-176954e2bb73
description: IMAPIWaitResult
Last modified: "April 26, 2021"
---

# IMAPIWAITRESULT : IUnknown
  
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
