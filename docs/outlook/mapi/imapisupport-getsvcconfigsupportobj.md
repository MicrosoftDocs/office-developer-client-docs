---
title: "IMAPISupportGetSvcConfigSupportObj"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.GetSvcConfigSupportObj
api_type:
- COM
ms.assetid: 56c3bdae-a3a8-4334-b6d2-a89c6820d72e
---

# IMAPISupport::GetSvcConfigSupportObj

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a message service support object.
  
```cpp
HRESULT GetSvcConfigSupportObj(
  ULONG ulFlags,
  LPMAPISUP FAR * lppSvcSupport
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lppSvcSupport_
  
> [out] A pointer to a pointer to the new message service support object.
    
## Return value

S_OK 
  
> The configuration support object was successfully created.
    
## Remarks

The **IMAPISupport::GetSvcConfigSupportObj** method is implemented for all support objects. Service providers call **GetSvcConfigSupportObj** to create a configuration support object to pass to a message service entry point function. 
  
A message service entry point function is based on the [MSGSERVICEENTRY](msgserviceentry.md) prototype and is called by methods of the [IMsgServiceAdmin](imsgserviceadminiunknown.md) interface. A message service entry point function allows message services to configure themselves or perform other actions when the profile is changed. Message service entry point functions can support configuration changes by displaying a property sheet or through a property value array passed to the [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md) method. 
  
## See also



[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)
  
[IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md)
  
[IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md)
  
[IProfAdmin : IUnknown](iprofadminiunknown.md)
  
[MSGSERVICEENTRY](msgserviceentry.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

