---
title: "DBEngine.SetOption Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1088781
  
localization_priority: Normal
ms.assetid: ea55c10c-2385-1b7e-0cba-32982c9b6643
description: "Temporarily overrides values for the Microsoft Access database engine keys in the Windows Registry (Microsoft Access workspaces only)."
---

# DBEngine.SetOption Method (DAO)

Temporarily overrides values for the Microsoft Access database engine keys in the Windows Registry (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **SetOption**( ** *Option* **, ** *Value* ** ) 
  
 *expression*  An expression that returns a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Option_ <br/> |Required  <br/> |**Long** <br/> |A constant as described in Remarks.  <br/> |
| _Value_ <br/> |Required  <br/> |**Variant** <br/> |The value that you want to set  _option_ to.  <br/> |
   
## Remarks

Each constant refers to the corresponding registry key in the path HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\12.0\Access Connectivity Engine\Engines\ACE (that is, **dbSharedAsyncDelay** corresponds to the key HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\12.0\Access Connectivity Engine\Engines\ACE\SharedAsyncDelay, and so on). 
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbPageTimeout** <br/> |The PageTimeout key  <br/> |
|**dbSharedAsyncDelay** <br/> |The SharedAsyncDelay key  <br/> |
|**dbExclusiveAsyncDelay** <br/> |The ExclusiveAsyncDelay key  <br/> |
|**dbLockRetry** <br/> |The LockRetry key  <br/> |
|**dbUserCommitSync** <br/> |The UserCommitSync key  <br/> |
|**dbImplicitCommitSync** <br/> |The ImplicitCommitSync key  <br/> |
|**dbMaxBufferSize** <br/> |The MaxBufferSize key  <br/> |
|**dbMaxLocksPerFile** <br/> |The MaxLocksPerFile key  <br/> |
|**dbLockDelay** <br/> |The LockDelay key  <br/> |
|**dbRecycleLVs** <br/> |The RecycleLVs key  <br/> |
|**dbFlushTransactionTimeout** <br/> |The FlushTransactionTimeout key  <br/> |
   
Use the **SetOption** method to override registry values at run-time. New values established with the **SetOption** method remain in effect until changed again by another **SetOption** call, or until the **DBEngine** object is closed. 
  

