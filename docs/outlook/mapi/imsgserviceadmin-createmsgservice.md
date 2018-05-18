---
title: "IMsgServiceAdminCreateMsgService"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgServiceAdmin.CreateMsgService
api_type:
- COM
ms.assetid: 0135f049-0311-45e5-9685-78597d599a4e
description: "Last modified: March 09, 2015"
---

# IMsgServiceAdmin::CreateMsgService

  
  
**Applies to**: Outlook 
  
Deprecated: The use of [IMsgServiceAdmin2::CreateMsgServiceEx](imsgserviceadmin2-createmsgserviceex.md) is recommended. Adds a message service to the current profile. 
  
```cpp
HRESULT CreateMsgService(
  LPSTR lpszService,
  LPSTR lpszDisplayName,
  ULONG_PTR ulUIParam,
  ULONG ulFlags    
);
```

## Parameters

 _lpszService_
  
> [in] A pointer to the name of the message service to add. This message service name must appear in the **[Services]** section of the MapiSvc.inf file. 
    
 _lpszDisplayName_
  
> [in] A pointer to the display name of the message service to add. The  _lpszDisplayName_ parameter is ignored if the message service has set the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property in the MapiSvc.inf file.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the message service is installed. The following flags can be set:
    
MAPI_UNICODE
  
> The lpszService and the lpszDisplayName parameters should be cast to LPWSTR and interpreted as Unicode strings.
    
SERVICE_NO_RESTART_WARNING
  
> When adding a new message service to the profile, the MAPI subsystem, based on various circumstances and criteria, often determines that this action requires a restart of Outlook. If the SERVICE_NO_RESTART_WARNING flag is not included and UI is allowed - based on the SERVICE_UI_ALWAYS and SERVICE_UI_ALLOWED flags - and at least one process is logged onto the current profile, this function displays the message "You must restart Outlook for these changes to take effect." Including the SERVICE_NO_RESTART_WARNING flag suppresses the display of that warning message.
    
SERVICE_UI_ALLOWED
  
> The message service configuration UI is allowed if needed.
    
SERVICE_UI_ALWAYS 
  
> The message service displays its configuration property sheet.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NOT_FOUND 
  
> The message service name is not in the **[Services]** section of MapiSvc.inf. 
    
## Remarks

The **IMsgServiceAdmin::CreateMsgService** method adds a message service to the current profile. **CreateMsgService** calls the message service's entry point function to perform any service-specific configuration tasks. If the SERVICE_UI_ALLOWED flag is set in the  _ulFlags_ parameter, the message service being installed can display a property sheet to enable the user to configure its settings. 
  
The MapiSvc.inf file contains the list of providers that make up a message service and the properties for each. **CreateMsgService** first creates a new profile section for the message service and then copies all of the information for that service from the MapiSvc.inf file into the profile, creating new sections for each provider. 
  
After all the information has been copied from MapiSvc.inf, the message service's entry point function is called with the MSG_SERVICE_CREATE value set in the  _ulContext_ parameter. If the SERVICE_UI_ALLOWED flag is set in the **CreateMsgService** method's  _ulFlags_ parameter, the values in the  _ulUIParam_ and  _ulFlags_ parameters are also passed when the message service's entry point function is called. Service providers should display their configuration property sheets so users can configure the message service. 
  
## Notes to callers

 **CreateMsgService** does not return the [MAPIUID](mapiuid.md) structure for the message service that was added to the profile. 
  
To retrieve the **MAPIUID** for the created message service, use the following procedure: 
  
1. Call the [IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md) method to get the message service administration table. 
    
2. Locate the row that represents the message service by placing a restriction on the table that matches the **PR_SERVICE_NAME** ([PidTagServiceName](pidtagservicename-canonical-property.md)) property with the name of the message service. 
    
3. Retrieve the service's **PR_SERVICE_UID** ([PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property. 
    
4. Pass the value of the **PR_SERVICE_UID** property in the  _lpUid_ parameter to the [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md) method to configure the service. 
    
> [!CAUTION]
> The Microsoft Outlook 2010 implementation of the MAPI subsystem does not support MAPI_UNICODE and will fail if it is used. 
  
> [!IMPORTANT]
> The  _ulFlags_ SERVICE_NO_RESTART_WARNING might not be defined in the downloadable header file you currently have, in which case you can add it to your code using the following value: >  `#define SERVICE_NO_RESTART_WARNING 0x00000080`
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProfileFunctions.cpp  <br/> |HrAddServiceToProfile  <br/> |MFCMAPI uses the **IMsgServiceAdmin::CreateMsgService** method to add a service to a profile.  <br/> |
   
## See also



[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

