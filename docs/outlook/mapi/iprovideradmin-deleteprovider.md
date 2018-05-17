---
title: "IProviderAdminDeleteProvider"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin.DeleteProvider
api_type:
- COM
ms.assetid: 0065b50f-95f6-4af1-81c2-a73e5111eecf
description: "Last modified: July 23, 2011"
---

# IProviderAdmin::DeleteProvider

  
  
**Applies to**: Outlook 
  
Deletes a service provider from the message service.
  
```
HRESULT DeleteProvider(
  LPMAPIUID lpUID
);
```

## Parameters

 _lpUID_
  
> [in, out] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier that represents the provider to delete. 
    
## Return value

S_OK 
  
> The provider was successfully deleted from the message service.
    
MAPI_E_NOT_FOUND 
  
> The **MAPIUID** pointed to by the  _lpUID_ parameter was not recognized. 
    
## Remarks

The **IProviderAdmin::DeleteProvider** method deletes a service provider from the message service. **DeleteProvider** determines the service provider to delete by matching the **MAPIUID** structure pointed to by  _lpUID_ with the set of identifiers registered by the active service providers. 
  
Most message services do not allow providers to be deleted while the profile is in use. If the provider to delete is in use, **DeleteProvider** marks it for deletion instead of removing it immediately and returns S_OK. When the provider is no longer being used, it is deleted. 
  
 **DeleteProvider** calls the message service's entry point function before the provider is removed from the service. The  _ulContext_ parameter is set to MSG_SERVICE_PROVIDER_DELETE. The message service entry point function performs the following tasks: 
  
- Deletes the service provider.
    
- Deletes the service provider's profile section.
    
The message service entry point function is not called again after the provider has been deleted.
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[MSGSERVICEENTRY](msgserviceentry.md)
  
[IProviderAdmin : IUnknown](iprovideradminiunknown.md)

