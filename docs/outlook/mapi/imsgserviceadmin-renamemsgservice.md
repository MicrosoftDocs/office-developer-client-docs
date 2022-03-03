---
title: "IMsgServiceAdminRenameMsgService"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.RenameMsgService
api_type:
- COM
ms.assetid: eba0e7f2-03c1-4713-aa36-3d0b398cd197
---

# IMsgServiceAdmin::RenameMsgService

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Deprecated. Assigns a new name to a message service. 
  
```cpp
HRESULT RenameMsgService(
  LPMAPIUID lpUID,
  ULONG ulFlags,
  LPSTR lpszDisplayName
);
```

## Parameters

 _lpUID_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier for the message service to rename. 
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpszDisplayName_
  
> [in] A pointer to the new name for the message service.
    
## Return value

MAPI_E_NO_SUPPORT 
  
> MAPI does not support renaming this message service. **RenameMsgService** always returns this value. 
    
## Remarks

To assign a new name to a message service, clients should use the **PR_SERVICE_NAME** ([PidTagServiceName](pidtagservicename-canonical-property.md)) property of the message service. The names of service providers in a message service are stored in their **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) properties. 
  
## See also



[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)

