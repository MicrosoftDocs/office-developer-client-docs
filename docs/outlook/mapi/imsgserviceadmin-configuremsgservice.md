---
title: "IMsgServiceAdminConfigureMsgService"
description: "Describes the syntax, parameters, return value, and remarks for IMsgServiceAdminConfigureMsgService, which reconfigures a message service."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.ConfigureMsgService
api_type:
- COM
ms.assetid: a08f5905-2585-49ca-abb7-a77f2736f604
---

# IMsgServiceAdmin::ConfigureMsgService

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Reconfigures a message service.
  
```cpp
HRESULT ConfigureMsgService(
  LPMAPIUID lpUID,
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  ULONG cValues,
  LPSPropValue lpProps
);
```

## Parameters

 _lpUID_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier for the message service to configure. 
    
 _ulUIParam_
  
> [in] A handle to the parent window of the configuration property sheet.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the display of the property sheet. The following flags can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
MSG_SERVICE_UI_READ_ONLY 
  
> The message service should display its configuration property sheet but not enable the user to change it. Most message services ignore this flag.
    
SERVICE_UI_ALLOWED 
  
> The message service should display its configuration property sheet only if the service is not completely configured.
    
SERVICE_UI_ALWAYS 
  
> The message service must always display its configuration property sheet. If SERVICE_UI_ALWAYS is not set, a configuration property sheet can still be displayed if SERVICE_UI_ALLOWED is set and valid configuration information is not available from the property value array in the _lpProps_ parameter. Either SERVICE_UI_ALLOWED or SERVICE_UI_ALWAYS must be set for a property sheet to be displayed. 
    
 _cValues_
  
> [in] The count of property values in the [SPropValue](spropvalue.md) structure pointed to by  _lpProps_. 
    
 _lpProps_
  
> [in] A pointer to an array of property values that describe the properties to display in the property sheet. The  _lpProps_ parameter should not be NULL if the message service should be configured without a user interface. 
    
## Return value

S_OK 
  
> The message service was successfully configured.
    
MAPI_E_EXTENDED_ERROR 
  
> An error specific to a message service. To get the [MAPIERROR](mapierror.md) structure that describes the error, the client application should call the [IMsgServiceAdmin::GetLastError](imsgserviceadmin-getlasterror.md) method. 
    
MAPI_E_NOT_FOUND 
  
> The **MAPIUID** pointed to by  _lpUID_ does not match that of an existing message service. 
    
MAPI_E_NOT_INITIALIZED 
  
> The message service does not have an entry point function.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in the property sheet. 
    
## Remarks

The **IMsgServiceAdmin::ConfigureMsgService** method enables a message service to be configured, with or without a configuration property sheet. 
  
To allow configuration without a property sheet display, message services typically prepare a header file that includes constants for all the required and optional properties and their values.
  
## Notes to callers

To retrieve the **MAPIUID** structure for the message service to configure, retrieve the **PR_SERVICE_UID** ([PidTagServiceUid](pidtagserviceuid-canonical-property.md)) column from the message service's row in the message service table. For more information, see the procedure outlined in the [IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md) method. 
  
You can configure a message service without displaying a property sheet to a user only if you have advance information about the property values to be set. If you are configuring a message service without displaying a property sheet, pass valid property values in the _lpProps_ parameter and do not set the MSG_SERVICE_UI_READ_ONLY, SERVICE_UI_ALLOWED, or SERVICE_UI_ALWAYS flags. 
  
If you receive all or some of the configuration information from the user by way of a property sheet, set SERVICE_UI_ALLOWED in  _ulFlags_. If you use existing property information only to establish default settings and the user is able to change the settings, set SERVICE_UI_ALWAYS in  _ulFlags_.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProfileFunctions.cpp  <br/> |HrAddServiceToProfile  <br/> |MFCMAPI uses the **IMsgServiceAdmin::ConfigureMsgService** method to configure a service that has been added to a profile. |
   
## See also



[MAPIUID](mapiuid.md)
  
[SPropValue](spropvalue.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

