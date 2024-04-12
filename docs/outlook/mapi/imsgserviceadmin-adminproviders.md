---
title: "IMsgServiceAdminAdminProviders"
description: "IMsgServiceAdminAdminProviders returns a pointer that provides access to a provider administration object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.AdminProviders
api_type:
- COM
ms.assetid: 0d605e2c-10db-46e1-95d5-12fabd524baa
---

# IMsgServiceAdmin::AdminProviders

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer that provides access to a provider administration object.
  
```cpp
HRESULT AdminProviders(
  LPMAPIUID lpUID,
  ULONG ulFlags,
  LPPROVIDERADMIN FAR * lppProviderAdmin
);
```

## Parameters

 _lpUID_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier for the message service to be administered. 
    
 _ulFlags_
  
> [in] Always NULL. 
    
 _lppProviderAdmin_
  
> [out] A pointer to a pointer to a provider administration object.
    
## Return value

S_OK 
  
> The provider administration object was successfully returned.
    
MAPI_E_NOT_FOUND 
  
> The **MAPIUID** pointed to by  _lpUID_ does not exist. 
    
## Remarks

The **IMsgServiceAdmin::AdminProviders** method provides access to a provider administration object. A provider administration is an object that supports the [IProviderAdmin](iprovideradminiunknown.md) interface and enables clients to do the following: 
  
- Add service providers to a message service.
    
- Delete service providers from a message service.
    
- Open profile sections.
    
- Access the message service provider table.
    
The types of changes that can actually be made to a message service while the profile is in use depend on the message service. However, most message services do not support changes such as adding and deleting providers while the profile is in use.
  
## Notes to callers

To retrieve the **MAPIUID** structure for the message service to administer, retrieve the **PR_SERVICE_UID** ([PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property column from the message service's row in the message service table. For more information, see the procedure outlined in the [IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md) method. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgServiceTableDlg.cpp  <br/> |CMsgServiceTableDlg::OnDisplayItem  <br/> |MFCMAPI uses the **IMsgServiceAdmin::AdminProviders** method to open a provider administration object for a service. |
   
## See also



[IProviderAdmin : IUnknown](iprovideradminiunknown.md)
  
[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

