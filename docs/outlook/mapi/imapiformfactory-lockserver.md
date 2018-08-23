---
title: "IMAPIFormFactoryLockServer"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormFactory.LockServer
api_type:
- COM
ms.assetid: b9bd389a-6975-41a2-a2f4-e501312e434b
description: "Last modified: July 23, 2011"
---

# IMAPIFormFactory::LockServer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Keeps an open form server in memory.
  
```cpp
HRESULT LockServer(
  ULONG ulFlags,
  ULONG fLockServer
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _fLockServer_
  
> [in] **true** to increment the lock count; otherwise, **false**.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form viewers call the **IMAPIFormFactory::LockServer** method to keep an open form server application in memory. Keeping the form server in memory improves its performance when forms are frequently created and released. 
  
## Notes to implementers

The **IMAPIFormFactory::LockServer** method is very similar to the [IClassFactory::LockServer](http://msdn.microsoft.com/en-us/library/ms682332%28v=VS.85%29.aspx) method. Essentially, the **IMAPIFormFactory::LockServer** method maintains a count of how many times it has been called; as long as that count is greater than 0, the method prevents the form server from being unloaded from memory. You can use the [CoLockObjectExternal](http://msdn.microsoft.com/en-us/library/ms680592%28VS.85%29.aspx) function to implement this. 
  
## See also



[IMAPIFormFactory : IUnknown](imapiformfactoryiunknown.md)

