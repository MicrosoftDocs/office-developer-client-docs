---
title: "IMAPIInitMoniter : IUnknown"  
manager: lindalu
ms.date: 03/30/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIInitMoniter
api_type:
- COM
ms.assetid: ad71ea65-394d-4be2-a9da-cd23099bc2cc
description: IMAPIInitMonitor
Last modified: "March 30, 2021"
---

# IMAPIInitMonitor : IUnknown

**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019

There are times when an application which consumes MAPI might want to know when the initialization is completed. For example, it have multiple threads which could initialize MAPI, or in response to MAPI being initialize the application would like perform some work, but does not want to always spin up the MAPI stack.  The initialization monitor provides this functionality through a function (exported from OLMAPI32.DLL).

| quick info | result |
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> | OLMAPI32.DLL <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIINITMONITOR  <br/> |

## Vtable order

| function | description |
|:-----|:-----|
|[IMAPIInitMonitor::IsInitialized](imapiinitmonitor-isinitialized.md) <br/> |Returns the current state of MAPI initialization.  <br/> |
|[IMAPIInitMonitor::Wait](imapiinitmonitor-wait.md) <br/> |Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized.  INFINITE can be used to for an infinite wait.  <br/> |
|[IMAPIInitMonitor::BeginWait](imapiinitmonitor-beginwait.md) <br/> |Start a wait for MAPI initialization or the specified number of milliseconds to elapse. This return an IMAPIWaitResult interface which should have “End” called in order begin the wait.  This allows the caller to control which thread is blocked while we are waiting. <br/> |

#### HRESULT STDAPICALLTYPE CreateMapiInitializationMonitor(IMAPIInitMonitor** ppInitMonitor)

This is entry point exported from OLMAPI32.DLL this allows the caller to retrieve an interface to query the current initialization state, setup a callback for initialization completion or block the current thread until has completed. The object returned from this API is reusable and thread safe and can be invoked from any thread, not just thread which retrieved it. Also, unlike other objects exposed from MAPI, this object is valid as long as the DLL is loaded, it can be re-used across initialization sessions and can be consumed before or after MAPIInitialize has been called. Returns success or failure through an COM standard HRESULT, and assigns an out parameter to an instance of IMAPIInitMonitor.

## See also
[IMAPIWaitResult : IUnknown](imapiwaitresultiunknown.md)
