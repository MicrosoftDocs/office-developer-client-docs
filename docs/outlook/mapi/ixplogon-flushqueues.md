---
title: "IXPLogonFlushQueues"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon.FlushQueues
api_type:
- COM
ms.assetid: c1f630c6-9e95-49c0-9757-4685c98184dc
description: "Last modified: July 23, 2011"
---

# IXPLogon::FlushQueues

  
  
**Applies to**: Outlook 
  
Requests that the transport provider immediately deliver all pending inbound or outbound messages.
  
```
HRESULT FlushQueues(
  ULONG_PTR ulUIParam,
  ULONG cbTargetTransport,
  LPENTRYID lpTargetTransport,
  ULONG ulFlags
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays.
    
 _cbTargetTransport_
  
> [in] Reserved; must be zero.
    
 _lpTargetTransport_
  
> [in] Reserved; must be NULL.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how message queue flushing is accomplished. The following flags can be set:
    
FLUSH_DOWNLOAD 
  
> The inbound message queue or queues should be flushed.
    
FLUSH_FORCE 
  
> The transport provider should process this request, if possible, even if doing so is time consuming. 
    
FLUSH_NO_UI 
  
> The transport provider should not display a user interface.
    
FLUSH_UPLOAD 
  
> The outbound message queue or queues should be flushed.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The MAPI spooler calls the **IXPLogon::FlushQueues** method to advise the transport provider that the MAPI spooler is about to begin processing messages. The transport provider should call the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method to set an appropriate bit for its state in the **PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property of its status row. After updating its status row, the transport provider should return S_OK for the **FlushQueues** call. The MAPI spooler then starts sending messages, with the operation being synchronous to the MAPI spooler. 
  
To support its implementation of the [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method, the MAPI spooler calls **IXPLogon::FlushQueues** for all logon objects for active transport providers that are running in a profile session. When a transport provider's **FlushQueues** method is called as a result of a client application call to **IMAPIStatus::FlushQueues**, the message processing occurs asynchronously to the client.
  
## See also

#### Reference

[IMAPIStatus::FlushQueues](imapistatus-flushqueues.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

