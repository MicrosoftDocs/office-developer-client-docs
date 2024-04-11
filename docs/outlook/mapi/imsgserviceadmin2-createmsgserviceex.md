---
title: "IMsgServiceAdmin2CreateMsgServiceEx" 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin2.CreateMsgServiceEx
api_type:
- COM
ms.assetid: 4910dabd-9380-4fde-a440-5c64d74c0bba
---

# IMsgServiceAdmin2::CreateMsgServiceEx

**Applies to**: Outlook 2013 | Outlook 2016
  
Adds a message service to the current profile and returns that newly added service UID.
  
```cpp
HRESULT CreateMsgServiceEx(
  LPSTR lpszService,
  LPSTR lpszDisplayName,
  ULONG_PTR ulUIParam,
  ULONG ulFlags, 
  LPMAPIUID lpuidService
);
```

## Parameters

 _lpszService_

> [in] A pointer to the name of the message service to add. This message service name must appear in the **[Services]** section of the MapiSvc.inf file.

 _lpszDisplayName_

> [in] A pointer to the display name of the message service to add. The _lpszDisplayName_ parameter is ignored if the message service has set the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property in the MapiSvc.inf file.

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

 _lpuidService_

> [out] The pointer to the UID of the message service added.

## Return value

S_OK

> The call succeeded and has returned the expected value or values.

MAPI_E_NOT_FOUND

> The message service name is not in the **[Services]** section of MapiSvc.inf.

## Remarks

The **IMsgServiceAdmin2::CreateMsgServiceEx** method adds a message service to the current profile. **CreateMsgServiceEx** calls the message service's entry point function to perform any service-specific configuration tasks. If the SERVICE_UI_ALLOWED flag is set in the _ulFlags_ parameter, the message service being installed can display a property sheet enabling the user to configure its settings.

The MapiSvc.inf file contains the list of providers that make up a message service and the properties for each. **CreateMsgServiceEx** first creates a new profile section for the message service and then copies all of the information for that service from the MapiSvc.inf file into the profile, creating new sections for each provider.

After all the information has been copied from MapiSvc.inf, the message service's entry point function, **MSGSERVICEENTRY**, is called with the MSG_SERVICE_CREATE value set in the _ulContext_ parameter. If the SERVICE_UI_ALLOWED flag is set in the **CreateMsgServiceEx** method's _ulFlags_ parameter, the values in the _ulUIParam_ and _ulFlags_ parameters are also passed when the message service's entry point function is called. Service providers should display their configuration property sheets so users can configure the message service.

## Notes to callers

If the **CreateMsgServiceEx** _lpuidService_ argument is not NULL, the **PR_SERVICE_UID** ([PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property of the message service that was added to the profile is returned in the **GUID** to which it points.

Pass the value of the **PR_SERVICE_UID** property in the _lpuidService_ parameter to the [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md) method to configure the service.

> [!CAUTION]
> The Microsoft Outlook 2010 implementation of the MAPI subsystem does not support MAPI_UNICODE and will fail if it is used.

> [!IMPORTANT]
> The IMsgServiceAdmin2 interface is exposed by the same object that implements the IMsgServiceAdmin interface, and has been available using Outlook's implementation of the MAPI subsystem since Outlook 2003. Its IID is defined as follows:
> `#if !defined(INITGUID) || defined(USES_IID_IMsgServiceAdmin2)`
> `DEFINE_OLEGUID(IID_IMsgServiceAdmin2,0x00020387, 0, 0);`> The _ulFlags_ SERVICE_NO_RESTART_WARNING might not be defined in the downloadable header file you currently have, in which case you can add it to your code using the following value: 
> `#define SERVICE_NO_RESTART_WARNING 0x00000080`
  
## See also

[IMsgServiceAdmin2 : IMsgServiceAdmin](imsgserviceadmin2imsgserviceadmin.md)
[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
