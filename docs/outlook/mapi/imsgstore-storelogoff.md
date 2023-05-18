---
title: "IMsgStoreStoreLogoff" 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.StoreLogoff
api_type:
- COM
ms.assetid: 3773c98e-531e-4bdc-a39a-2c3bb7378cd3
---

# IMsgStore::StoreLogoff
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables the orderly logoff of the message store.
  
```cpp
HRESULT StoreLogoff(
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [in, out] A bitmask of flags that controls logoff from the message store. On input, all flags set for this parameter are mutually exclusive; a caller must specify only one flag per call. The following flags are valid on input:
    
LOGOFF_ABORT 
  
> Any transport provider activity for this message store should be stopped before logoff. Control is returned to the caller after activity is stopped. If any transport provider activity is taking place, the logoff does not occur and no change in the behavior of the MAPI spooler or transport providers occurs. If transport provider activity is idle, the MAPI spooler releases the store. 
    
LOGOFF_NO_WAIT 
  
> The message store should not wait for messages from transport providers before closing. Outbound messages that are ready to be sent are sent. If this store contains the default Inbox, any in-process messages are received, and then further reception is disabled. When all activity is complete, the MAPI spooler releases the store, and control is immediately returned to the caller. 
    
LOGOFF_ORDERLY 
  
> The message store should not wait for information from transport providers before closing. Messages that are currently being processed are completed, but no new messages are processed. When all activity is complete, the MAPI spooler releases the store, and control is immediately returned to the store provider. 
    
LOGOFF_PURGE 
  
> The logoff should work the same as if the LOGOFF_NO_WAIT flag is set, but either the [IXPLogon::FlushQueues](ixplogon-flushqueues.md) or [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method for the appropriate transport providers should be called. The LOGOFF_PURGE flag returns control to the caller after completion. 
    
LOGOFF_QUIET 
  
> If any transport provider activity is taking place, the logoff should not occur.
    
The following flags are valid on output
    
LOGOFF_INBOUND 
  
> Inbound messages are currently arriving.
    
LOGOFF_OUTBOUND 
  
> Outbound messages are in the process of being sent.
    
LOGOFF_OUTBOUND_QUEUE 
  
> Outbound messages are pending (that is, they are in the Outbox).
    
## Return value

S_OK 
  
> The logoff completed successfully.
    
## Remarks

The **IMsgStore::StoreLogoff** method exerts control over the interaction of the message store and transport providers during the logoff process. Calling **StoreLogoff** is valid only for message stores that are being used only by the caller. For example, when two clients are using the same message store and one of them calls **StoreLogoff**, the message store is immediately released and control is returned to the calling client.
  
## Notes to implementers

Save the flags that are passed to **StoreLogoff** and pass them when you call the [IMAPISupport::StoreLogoffTransports](imapisupport-storelogofftransports.md) method. Do not call **StoreLogoffTransports** until the message store's reference count drops to zero. Multiple calls to **StoreLogoffTransports** simply overwrite the saved flags. 
  
If no call has been made to **StoreLogoff** before the message store's reference count reaches zero, set the LOGOFF_ABORT flag in the _ulFlags_ parameter that you pass to **StoreLogoffTransports**.
  
## See also



[IMAPIStatus::FlushQueues](imapistatus-flushqueues.md)
  
[IMAPISupport::StoreLogoffTransports](imapisupport-storelogofftransports.md)
  
[IXPLogon::FlushQueues](ixplogon-flushqueues.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)

