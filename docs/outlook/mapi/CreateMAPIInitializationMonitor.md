---
title: "CreateMAPIInitializationMonitor" 
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
ms.assetid: 32a9758a-395d-4526-9610-3e4eeaf78c96
description: MAPI Initialization Monitor
Last modified: "April 26, 2021"
---

# CreateMAPIInitializationMonitor

**Applies to**: Outlook 2016 | Outlook 2019
  
## MAPI Initialization Monitor

There are times when an application which consumes MAPI might want to know when the initialization is completed. For example, it have multiple threads which could initialize MAPI, or in response to MAPI being initialize the application would like perform some work, but does not want to always spin up the MAPI stack. The initialization monitor provides this functionality through a function (exported from OLMAPI32.DLL) and a couple of simple interfaces described below.

This is entry point exported from OLMAPI32.DLL this allows the caller to retrieve an interface to query the current initialization state, setup a callback for initialization completion or block the current thread until has completed. The object returned from this API is reusable and thread safe and can be invoked from any thread, not just thread which retrieved it. Also, unlike other objects exposed from MAPI, this object is valid as long as the DLL is loaded, it can be re-used across initialization sessions and can be consumed before or after MAPIInitialize has been called. Returns success or failure through an COM standard HRESULT, and assigns an out parameter to an instance of IMAPIInitMonitor.

```cpp
HRESULT CreateMAPIInitializationMonitor(IMAPIInitMonitor** ppInitMonitor); 
```
#### HRESULT STDAPICALLTYPE CreateMapiInitializationMonitor(IMAPIInitMonitor ppInitMonitor)

This entry point exported from OLMAPI32.DLL allows the caller to retrieve an interface to query the current initialization state, setup a callback for initialization completion or block the current thread until has completed. The object returned from this API is reusable and thread safe and can be invoked from any thread, not just thread which retrieved it. Also, unlike other objects exposed from MAPI, this object is valid as long as the DLL is loaded, it can be re-used across initialization sessions and can be consumed before or after MAPIInitialize has been called. Returns success or failure through an COM standard HRESULT, and assigns an out parameter to an instance of IMAPIInitMonitor.
  
## Quick info

| identifier | result |
|:-----|:-----|
|Exported by:  <br/> |olmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |

## Quick info

| identifier | result |
|:-----|:-----|
|Exported by:  <br/> |olmapi32.dll  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |


## Parameters
  
 _ppInitMonitor_
> [out] A pointer to receive the newly created instance of the MAPI initialization monitor.
  
## Return values

S_OK
> A new instance of the initialization monitor was created successfully.

E_OUTOFMEMORY
> There was not enough memory to crate a new object.

## See also
[IMAPIInitMonitor](imapiinitmonitoriunknown.md)

[IMAPIWaitResult](imapiwaitresultiunknown.md)
