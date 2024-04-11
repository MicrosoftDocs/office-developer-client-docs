---
title: "IMAPISupportStoreLogoffTransports" 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.StoreLogoffTransports
api_type:
- COM
ms.assetid: f21fba96-c5ca-4d41-9b93-c7955ab7327f
---

# IMAPISupport::StoreLogoffTransports
 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Requests the orderly release of a message store.
  
```cpp
HRESULT StoreLogoffTransports(
ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [in, out] A bitmask of flags that controls how message store logoff occurs. On input, all flags for this parameter are mutually exclusive; only one of the following flags can be set per call:
    
LOGOFF_ABORT 
  
> Any transport provider activity for this store should be stopped before logoff. Control is returned to the client after the activity is stopped and the MAPI spooler has logged off the store. If any transport activity is taking place, the logoff does not occur and no change in the MAPI spooler or transport provider behavior occurs. If there is currently no activity, the MAPI spooler releases the store. 
    
LOGOFF_NO_WAIT 
  
> The MAPI spooler should release the store and return control to the client immediately after all outbound mail that is ready to be sent is sent. If the message store has the default Inbox, any in-process message is received, and then further reception is disabled. 
    
LOGOFF_ORDERLY 
  
> The MAPI spooler should release the store and return control to the client immediately after any pending messages are finished processing. No new messages should be processed. 
    
LOGOFF_PURGE 
  
> Works the same as the LOGOFF_NO_WAIT flag. The LOGOFF_PURGE flag returns control to the caller after completion. 
    
LOGOFF_QUIET 
  
> The logoff should not occur if any transport provider activity is taking place. The type of activity taking place is returned as a flag on output.

On output, MAPI spooler can return one or more of the following flags:
    
LOGOFF_COMPLETE 
  
> The logoff can complete. All resources associated with the store have been released, and the object has been invalidated. The MAPI spooler has performed or will perform all requests. Only the message store's **IUnknown::Release** method should be called at this point. 
    
LOGOFF_INBOUND 
  
> A message is currently coming into the store from one or more transport providers. 
    
LOGOFF_OUTBOUND 
  
> A message is currently being sent from the store by one or more transport providers. 
    
LOGOFF_OUTBOUND_QUEUE 
  
> There are currently messages in the outbound queue for the store.
    
## Return value

S_OK 
  
> The logoff procedure was successful.
    
## Remarks

The **IMAPISupport::StoreLogoffTransports** method is implemented for message store provider support objects. Message store providers call **StoreLogoffTransports** to give client applications some control over how MAPI handles transport provider activity as a message store is closing. 
  
If another process has the store to be logged off open for the same profile, MAPI ignores a call to **StoreLogoffTransports** and returns the flag LOGOFF_COMPLETE in the _lpulFlags_ parameter. 
  
The behavior of the store provider following the return from **StoreLogoffTransports** should be based on the value of  _lpulFlags_, which indicates system status and conveys client instructions for logoff behavior. 
  
## Notes to callers

 **StoreLogoffTransports** is typically called from a store provider's [IMsgStore::StoreLogoff](imsgstore-storelogoff.md) method. However, it can also be called from the **IUnknown::Release** method of the message store. Implement the **Release** method of your message store so you can check whether or not a call to **StoreLogoffTransports** has occurred. If a call has not occurred, call **StoreLogoffTransports** with the LOGOFF_ABORT flag set. 
  
The  _lpulFlags_ parameter is set to a flag that indicates how the client requires the message store to be shut down. Determine the appropriate setting for  _ulFlags_ based on the setting of the corresponding parameter in the call to **StoreLogoff**. That is, if a client called your **StoreLogoff** method with  _ulFlags_ set to LOGOFF_ORDERLY, you should call **StoreLogoffTransports** with  _ulFlags_ set to LOGOFF_ORDERLY. 
  
For more information about the message store logoff process, see [Shutting Down a Message Store Provider](shutting-down-a-message-store-provider.md).
  
## See also



[IMsgStore::StoreLogoff](imsgstore-storelogoff.md)
  
[IXPLogon::FlushQueues](ixplogon-flushqueues.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

