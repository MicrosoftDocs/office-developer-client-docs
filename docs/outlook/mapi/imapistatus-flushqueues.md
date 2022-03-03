---
title: "IMAPIStatusFlushQueues"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIStatus.FlushQueues
api_type:
- COM
ms.assetid: d6b01a91-b452-4b2c-9802-698e7b0f4169
---

# IMAPIStatus::FlushQueues

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Forces all messages waiting to be sent or received to be immediately uploaded or downloaded. The MAPI spooler status object and status objects that transport providers implement support this method.
  
```cpp
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
  
> [in] The byte count in the entry identifier pointed to by the  _lpTargetTransport_ parameter. The  _cbTargetTransport_ parameter is set only on calls to the MAPI spooler's status object. For calls to a transport provider, the  _cbTargetTransport_ parameter is set to 0. 
    
 _lpTargetTransport_
  
> [in] A pointer to the entry identifier of the transport provider that is to flush its message queues. The  _lpTargetTransport_ parameter is set only on calls to the MAPI spooler's status object. For calls to a transport provider, the  _lpTargetTransport_ parameter is set to NULL. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the flush operation. The following flags can be set:
    
FLUSH_ASYNC_OK 
  
> The flush operation can occur asynchronously. This flag applies only to the MAPI spooler's status object. 
    
FLUSH_DOWNLOAD 
  
> The incoming message queues should be flushed.
    
FLUSH_FORCE 
  
> The flush operation should occur regardless, in spite of the chance of a decrease in performance. This flag must be set when an asynchronous transport provider is targeted.
    
FLUSH_NO_UI 
  
> The status object should not display a progress indicator.
    
FLUSH_UPLOAD 
  
> The outgoing message queues should be flushed.
    
## Return value

S_OK 
  
> The flush operation was successful.
    
MAPI_E_BUSY 
  
> Another operation is in progress; it should be allowed to complete, or it should be stopped, before this operation can be initiated.
    
MAPI_E_NO_SUPPORT 
  
> The status object does not support this operation, as indicated by the absence of the STATUS_FLUSH_QUEUES flag in the status object's **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property.
    
## Remarks

The **IMAPIStatus::FlushQueues** method requests that the MAPI spooler or a transport provider immediately send all messages in the outgoing queue or receive all messages from the incoming queue. **FlushQueues** is implemented only by the MAPI spooler status object and by status objects that transport providers supply. 
  
MAPI_E_BUSY should be returned for asynchronous requests so that clients can continue work. 
  
By default, **FlushQueues** is a synchronous operation; control does not return to the caller until the flush has completed. Only the flush operation performed by the MAPI spooler can be asynchronous; clients request this behavior by setting the FLUSH_ASYNC_OK flag. 
  
## Notes to implementers

A remote transport provider's implementation of **FlushQueues** sets bits in the **PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property in the logon object's status row to control how queues are flushed. If a remote viewer passes in the FLUSH_UPLOAD flag, the **FlushQueues** method should set the STATUS_INBOUND_ENABLED and STATUS_INBOUND_ACTIVE bits. If a remote viewer passes in the FLUSH_DOWNLOAD flag, the **FlushQueues** method should set the STATUS_OUTBOUND_ENABLED and STATUS_OUTBOUND_ACTIVE bits. **FlushQueues** should then return S_OK. The MAPI spooler will then initiate the appropriate actions to upload and download messages. 
  
## Notes to callers

A call to the MAPI spooler status object is a directive to transfer all messages either to or from the appropriate transport provider. When you call an individual transport provider's status object, only the messages for that provider are affected.
  
## See also



[PidTagResourceMethods Canonical Property](pidtagresourcemethods-canonical-property.md)
  
[PidTagStatusCode Canonical Property](pidtagstatuscode-canonical-property.md)
  
[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)

