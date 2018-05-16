---
title: "IMAPISupportSpoolerNotify"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.SpoolerNotify
api_type:
- COM
ms.assetid: d4f153b2-939f-4153-85fb-dc510193848c
description: "Last modified: March 09, 2015"
---

# IMAPISupport::SpoolerNotify

  
  
**Applies to**: Outlook 
  
Notifies the MAPI spooler of a change in status or a request for service. 
  
```
HRESULT SpoolerNotify(
ULONG ulFlags,
LPVOID lpvData
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that indicates the type of notification. Transport providers can set all of the flags except for NOTIFY_NEWMAIL_RECEIVED; only NOTIFY_NEWMAIL_RECEIVED and NOTIFY_READTOSEND are valid for message store providers. The following flags are valid for the  _ulFlags_ parameter: 
    
NOTIFY_CONFIG_CHANGE 
  
> Registers a request to change the transport provider's configuration. 
    
NOTIFY_CRITICAL_ERROR 
  
> An unrecoverable error has occurred to the transport provider. Because both NOTIFY_SENTDEFERRED and NOTIFY_CRITICAL_ERROR use the  _lpvData_ parameter for transport provider calls, these flags are mutually exclusive. 
    
NOTIFY_CRITSEC 
  
> Requests a critical section for the transport provider. The  _lpvData_ parameter is undefined and should be NULL. 
    
NOTIFY_NEWMAIL 
  
> The MAPI spooler should download any newly received messages at the next available time. The  _lpvData_ parameter is undefined and should be set to NULL. 
    
NOTIFY_NEWMAIL_RECEIVED 
  
> A new message has been received in the message store. The  _lpvData_ parameter points to a [NEWMAIL_NOTIFICATION](newmail_notification.md) structure that describes the message. This flag is used for message store providers that are tightly coupled with transport providers and is ignored if the store provider is logged on with the MAPI_NO_MAIL flag set. 
    
NOTIFY_NONCRIT 
  
> Releases a critical section that was obtained with a previous call to **SpoolerNotify** with  _ulFlags_ set to NOTIFY_CRITSEC. The  _lpvData_ parameter is undefined and should be set to NULL. 
    
NOTIFY_READYTOSEND 
  
> The transport or message store provider is ready to send messages. The  _lpvData_ parameter is undefined and should be set to NULL. 
    
NOTIFY_SENTDEFERRED 
  
> A previously deferred message should now be sent, and the transport provider should be notified when the message is ready to be delivered by using a call to the [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) method. The entry identifier of the deferred message is contained in an [SBinary](sbinary.md) structure pointed to by  _lpvData_. Because both NOTIFY_SENTDEFERRED and NOTIFY_CRITICAL_ERROR use the  _lpvData_ parameter, these flags are mutually exclusive. 
    
 _lpvData_
  
> [in] A pointer to associated data applicable to a notification. The  _lpvData_ parameter points to valid data only when the following flags are set (  _lpvData_ is NULL when  _ulFlags_ is set to the other notification types): 
    
|**_ulFlags_ setting**|**_lpvData_ value**|
|:-----|:-----|
|NOTIFY_CRITICAL_ERROR  <br/> |Information about the error.  <br/> |
|NOTIFY_NEWMAIL_RECEIVED  <br/> |A **NEWMAIL_NOTIFICATION** structure that contains information about the newly delivered message.  <br/> |
|NOTIFY_SENTDEFERRED  <br/> |An **SBinary** structure that contains the entry identifier of deferred message.  <br/> |
   
## Return value

S_OK 
  
> The notification was successful.
    
## Remarks

The **IMAPISupport::SpoolerNotify** method is implemented for message store and transport provider support objects. These providers call **SpoolerNotify** to notify the MAPI spooler of a change in status or a request for service. **SpoolerNotify** is called primarily by transport providers and may be called at any time during the session. 
  
## Notes to Transport Providers

If you have changed your transport provider configuration, call **SpoolerNotify** and set  _ulFlags_ to NOTIFY_CONFIG_CHANGED. **SpoolerNotify** responds by calling the [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method to query for a change in supported address types. 
  
If you need a critical section to ensure uninterrupted processing, call **SpoolerNotify** with  _ulFlags_ set to NOTIFY_CRITSEC. Setting this flag informs the MAPI spooler that it should not call the [IXPLogon::Idle](ixplogon-idle.md) and [IXPLogon::Poll](ixplogon-poll.md) methods. While you have a critical section open, return MAPI_E_BUSY whenever the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method is called. When you are finished with the critical section, make another call to **SpoolerNotify** with  _ulFlags_ set to NOTIFY_NONCRIT. 
  
For example, if your remote transport provider is in the process of uploading messages, you might need to allow a user to enter a telephone number to establish the remote connection. Before you loop through the dialog box procedure, you should declare a critical section. When the user closes the dialog box, terminating the dialog box procedure, you should release the critical section.
  
When you set  _ulFlags_ to NOTIFY_CRITICAL_ERROR, the MAPI spooler makes no further calls to the provider except to release it. If you call **SpoolerNotify** with NOTIFY_CRITICAL_ERROR set from the [IXPLogon::StartMessage](ixplogon-startmessage.md) or [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) methods, return with an appropriate error value from the **StartMessage** or ** SubmitMessage ** call immediately after the **SpoolerNotify** call. 
  
If your transport provider recovered from a condition that previously caused it to fail, call **SpoolerNotify** with  _ulFlags_ set to NOTIFY_READYTOSEND. This flag indicates that the provider is again ready to handle messages. 
  
## Notes to Message Store Providers

Call **SpoolerNotify**, passing the NOTIFY_READYTOSEND flag in  _ulFlags_, before you make your first call to [IMAPISupport::PrepareSubmit](imapisupport-preparesubmit.md) in **IMessage::SubmitMessage**. This call to **SpoolerNotify** needs to be made only once per session. 
  
If your message store provider is tightly coupled with a transport provider and you call **SpoolerNotify** with  _ulFlags_ set to NOTIFY_NEWMAIL_RECEIVED, the MAPI spooler opens the new message and begins processing the new message hook function. When processing is complete, the MAPI spooler calls the [IMsgStore::NotifyNewMail](imsgstore-notifynewmail.md) method to inform you of your own new message. 
  
For more information about calling **SpoolerNotify**, see any of the following topics:
  
- [Implementing the FlushQueues Method](implementing-the-flushqueues-method.md)
    
- [Interacting with the MAPI Spooler](interacting-with-the-mapi-spooler.md)
    
- [Message Reception Model](message-reception-model.md)
    
## See also

#### Reference

[IMsgStore::NotifyNewMail](imsgstore-notifynewmail.md)
  
[IXPLogon::StartMessage](ixplogon-startmessage.md)
  
[IXPLogon::SubmitMessage](ixplogon-submitmessage.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

