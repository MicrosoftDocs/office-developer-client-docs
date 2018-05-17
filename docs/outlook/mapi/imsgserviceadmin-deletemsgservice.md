---
title: "IMsgServiceAdminDeleteMsgService"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgServiceAdmin.DeleteMsgService
api_type:
- COM
ms.assetid: 3a6b34eb-9d46-488f-8d02-91b27c35de67
description: "Last modified: March 09, 2015"
---

# IMsgServiceAdmin::DeleteMsgService

  
  
**Applies to**: Outlook 
  
Deletes a message service from a profile.
  
```
HRESULT DeleteMsgService(
  LPMAPIUID lpuid
);
```

## Parameters

 _lpuid_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier for the message service to delete. 
    
## Return value

S_OK 
  
> The message service was deleted.
    
MAPI_E_NOT_FOUND 
  
> The **MAPIUID** pointed to by  _lpuid_ does not match an existing message service. 
    
## Remarks

The **IMsgServiceAdmin::DeleteMsgService** method deletes a message service from a profile. **DeleteMsgService** removes all profile sections related to the message service. 
  
 **DeleteMsgService** performs the following steps to delete the message service: 
  
1. Calls the message service's entry point function with the  _ulContext_ parameter set to MSG_SERVICE_DELETE before the profile sections are removed. This allows the service to perform any service-specific tasks. 
    
2. Deletes the message service.
    
3. Deletes the message service's profile section.
    
The message service's entry point function is not called again after the service has been deleted.
  
## Notes to Callers

To retrieve the **MAPIUID** structure for the message service to delete, retrieve the **PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property column from the message service's row in the message service table. For more information, see the procedure outlined in the [IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md) method. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgServiceTableDlg.cpp  <br/> |CMsgServiceTableDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **IMsgServiceAdmin::DeleteMsgService** method to delete the selected service.  <br/> |
   
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

