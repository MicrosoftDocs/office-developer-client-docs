---
title: "IMAPIStatusValidateState"
description: "IMAPIStatusValidateState confirms the external status information available for the MAPI resource or the service provider."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIStatus.ValidateState
api_type:
- COM
ms.assetid: 036b9b15-86e1-4a37-8e4b-e37b2963d8fb
---

# IMAPIStatus::ValidateState

**Applies to**: Outlook 2013 | Outlook 2016 
  
Confirms the external status information available for the MAPI resource or the service provider. This method is supported in all status objects. 
  
```cpp
HRESULT ValidateState(
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

_ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays.
    
_ulFlags_
  
> [in] A bitmask of flags that controls the validation. The following flags can be set:
    
ABORT_XP_HEADER_OPERATION
  
> The user canceled the operation, typically by clicking the **Cancel** button in the corresponding dialog box. The status object has two options: 
    
   - Continue working on the operation.
    
   - Stop the operation and return MAPI_E_USER_CANCELED.
    
CONFIG_CHANGED 
  
> One or more of the status object's configuration properties changed. Clients can set this flag to allow the MAPI spooler to dynamically correct critical transport provider failures. 
    
FORCE_XP_CONNECT 
  
> The status object should perform a connection. When this flag is used with the REFRESH_XP_HEADER_CACHE or PROCESS_XP_HEADER_CACHE flag, the connection occurs without caching.
    
FORCE_XP_DISCONNECT 
  
> The status object should perform a disconnect operation. When this flag is used with the REFRESH_XP_HEADER_CACHE or PROCESS_XP_HEADER_CACHE flag, the disconnection occurs without caching.
    
PROCESS_XP_HEADER_CACHE 
  
> Entries in the header cache table should be processed, all messages marked with the MSGSTATUS_REMOTE_DOWNLOAD flag should be downloaded, and all messages marked with the MSGSTATUS_REMOTE_DELETE flag should be deleted. Messages that have both MSGSTATUS_REMOTE_DOWNLOAD and MSGSTATUS_REMOTE_DELETE set should be moved.
    
REFRESH_XP_HEADER_CACHE 
  
> For a remote transport provider, a new list of message headers should be downloaded and all flags that mark message status should be cleared.
    
SUPPRESS_UI 
  
> Prevents the status object from displaying a user interface as part of the operation.
    
## Return value

S_OK 
  
> The validation was successful.
    
MAPI_E_BUSY 
  
> Another operation is in progress; it should be allowed to complete, or it should be stopped, before this operation is initiated.
    
MAPI_E_NO_SUPPORT 
  
> The status object does not support the validation method, as indicated by the absence of the STATUS_VALIDATE_STATE flag in the **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the validation operation, typically by clicking the **Cancel** button in a dialog box. This value is returned only by remote transport providers. 
    
## Remarks

The **IMAPIStatus::ValidateState** method checks the state of a resource that is associated with a status object. **ValidateState** is the only method in the [IMAPIStatus](imapistatusimapiprop.md) interface that is required for all status objects. The exact behavior of this method depends on the implementation. The following table describes the implementation of each of the different types of status objects. 
  
|**Status object**|****ValidateState** implementation**|
|:-----|:-----|
|MAPI subsystem  <br/> |Validates the state of all the resources that the currently active service providers and the subsystem itself own. |
|MAPI spooler  <br/> |Performs a logon of all transport providers, regardless of whether they are already logged on. |
|MAPI address book  <br/> |Checks the entries in its profile section. |
|Service provider  <br/> |Implementation depends on the type of provider and the flags set in the _ulFlags_ parameter. |
   
## Notes to implementers

Remote client applications call the **ValidateState** method to start remote processing for various actions. This method exists primarily to set status bits to communicate with the MAPI spooler, instead of to actually do any work. Typically, the transport provider sets flags in its status row that indicate to the MAPI spooler what actions need to be initiated to complete the client's request. 

In this model of client-transport-spooler interaction, the actions requested by the client are asynchronous, in that **ValidateState** returns before the requested actions are complete. However, actions that do not necessarily involve the underlying messaging system, or that involve a transport-specific interface, can be synchronous. The client application passes in a bitmask of the following flags to specify which actions the remote transport provider should take. 
  
ABORT_XP_HEADER_OPERATION 
  
> If possible, the remote transport provider should cancel any operations that involve downloading headers. To do this, the transport provider must set the following property values in the logon object's status row:
    
   - Clear the STATUS_INBOUND_ENABLED and STATUS_INBOUND_ACTIVE bits in the **PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property to tell the MAPI spooler to halt the incoming flush process for this transport provider.
    
   - Set the STATUS_OFFLINE bit in the **PR_STATUS_CODE** property. 
    
   - Set the **PR_REMOTE_VALIDATE_OK** ([PidTagRemoteValidateOk](pidtagremotevalidateok-canonical-property.md)) property to TRUE.
    
   - Set the **PR_STATUS_STRING** ([PidTagStatusString](pidtagstatusstring-canonical-property.md)) property to a string that indicates the transport provider's status to the user.
    
   - Return S_OK. However, if the operation in progress cannot be canceled, **ValidateState** should return MAPI_E_BUSY. 
    
FORCE_XP_CONNECT 
  
> A remote transport provider should never establish a connection to a shared resource (for example, a modem or COM port) outside the context of the MAPI spooler-transport interaction involved in the [IXPLogon::FlushQueues](ixplogon-flushqueues.md) method. If **ValidateState** is called with this flag, your transport provider should do the following: 
    
   - Set an internal status flag to indicate that the remote connection must be established when the **IXPLogon::FlushQueues** method is called. 
    
   - Set the correct values in the status table to cause the MAPI spooler to initiate the queue flushing process.
    
   - When flushing of queues is complete, release the shared resource.
    
   - Clear the STATUS_OFFLINE bit in the **PR_STATUS_CODE** property. 
    
   - Return S_OK.
    
FORCE_XP_DISCONNECT 
  
> The remote transport provider should release its connection to the messaging system resources. After doing this, it should set the STATUS_OFFLINE bit in the **PR_STATUS_CODE** property and return S_OK. 
    
PROCESS_XP_HEADER_CACHE 
  
> The remote transport provider should process remote messages and upload any messages that have been deferred. To do this, the transport provider must set the following property values in the logon object's status row:
    
   - Set the **PR_STATUS_STRING** property to a string that indicates the transport provider's status to the user. 
    
   - Set the STATUS_OUTBOUND_ENABLED and STATUS_OUTBOUND_ACTIVE bits in the **PR_STATUS_CODE** property. 
    
   - Set the **PR_REMOTE_VALIDATE_OK** property in the transport provider's status row to FALSE. 
    
   - If another operation is in progress (such as downloading headers) when **ValidateState** is called, **ValidateState** should return MAPI_E_BUSY. 
    
   - Execute the code for processing the REFRESH_XP_HEADER_CACHE flag, as well, to satisfy requirements of the Microsoft Exchange client.
    
REFRESH_XP_HEADER_CACHE 
  
> The remote transport provider should retrieve any new message headers from the messaging system. To do this, the transport provider must do the following:
    
   - Set the **PR_STATUS_STRING** property to a string that indicates the transport provider's status to the user. 
    
   - Set the STATUS_INBOUND_ENABLED and STATUS_INBOUND_ACTIVE bits in the **PR_STATUS_CODE** property. 
    
   - Clear the STATUS_OFFLINE bit in the **PR_STATUS_CODE** property. 
    
   - Set the STATUS_ONLINE bit in the **PR_STATUS_CODE** property. 
    
   - Set the **PR_REMOTE_VALIDATE_OK** property in the transport provider's status row to FALSE. 
    
SHOW_XP_SESSION_UI 
  
> If your transport provider has any pieces of user interface for processing the message headers (such as a dialog box that confirms the downloading of messages), that dialog box should be displayed. Otherwise, **ValidateState** can return MAPI_E_NO_SUPPORT. 
    
If any flags other than these are passed in, **ValidateState** should return MAPI_E_UNKNOWN_FLAGS. 
  
The client's call to the transport provider will often be to the **IMAPIStatus::ValidateState** method. During the processing of **ValidateState**, the transport provider should not perform any actions that allocate scarce system resources, such as a modem or COM port. This is because the MAPI spooler will sometimes need to flush queues on more than one transport provider. However, the client can call any transport provider's **ValidateState** method at any time. If your transport provider attempts to allocate a scarce resource during the processing of **ValidateState**, an error can result due to conflict with another transport provider that the MAPI spooler has instructed to flush its queues. If you allow all scarce resource allocations to occur under the direction of the MAPI spooler, you can avoid such conflicts. Your transport provider should support the **PR_REMOTE_VALIDATE_OK** property so client applications can detect when your transport provider is busy or waiting for the MAPI spooler to initiate an action. 
  
## Notes to callers

Because this method can cause other potentially lengthy calls to be made, **ValidateState** can return MAPI_E_BUSY to inform you that this method is waiting for the completion of another operation. You should wait until the pending operation is complete before attempting another task. 
  
You have the most control over your calls to transport provider status objects. You can pass one or more flags to **ValidateState** that affect the transport provider's operations. For example, the ABORT_XP_HEADER_OPERATION flag indicates that the user canceled the validation. Transport providers can decide to abort, returning MAPI_E_USER_CANCELED, or can continue. 
  
You can set the CONFIG_CHANGED flag on a call to either the status object of a service provider or the MAPI spooler to indicate that a configuration option has been changed. You can use CONFIG_CHANGED to dynamically reconfigure a transport provider. When you set CONFIG_CHANGED on a call to a service provider's status object, the provider responds with a call to [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) to alert the MAPI spooler of the change. When you set CONFIG_CHANGED on a call to the MAPI spooler's status object, the spooler calls [IXPLogon::AddressTypes](ixplogon-addresstypes.md) for each active transport provider. **AddressTypes** informs the MAPI spooler of a transport's supported address types. Some service providers also display a progress indicator if the validation is expected to take a long time. Displaying a progress indicator is helpful, but not required. 
  
When the SUPPRESS_UI flag is set, none of the configuration property sheets or progress dialog boxes can be displayed. 
  
## See also

- [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md)
- [IXPLogon::AddressTypes](ixplogon-addresstypes.md)
- [IXPLogon::FlushQueues](ixplogon-flushqueues.md)
- [PidTagRemoteValidateOk Canonical Property](pidtagremotevalidateok-canonical-property.md)
- [PidTagResourceMethods Canonical Property](pidtagresourcemethods-canonical-property.md)
- [PidTagStatusCode Canonical Property](pidtagstatuscode-canonical-property.md)
- [PidTagStatusString Canonical Property](pidtagstatusstring-canonical-property.md)
- [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)

