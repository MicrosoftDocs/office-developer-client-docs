---
title: "IMAPISupportDoConfigPropsheet"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.DoConfigPropsheet
api_type:
- COM
ms.assetid: 3899c49c-a0ec-4dca-92e8-e801cd4908cf
description: "Last modified: July 23, 2011"
---

# IMAPISupport::DoConfigPropsheet

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Displays a configuration property sheet.
  
```cpp
HRESULT DoConfigPropsheet(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPSTR lpszTitle,
  LPMAPITABLE lpDisplayTable,
  LPMAPIPROP lpConfigData,
  ULONG ulTopPage
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the property sheet.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpszTitle_
  
> [in] A pointer to the title of the property sheet.
    
 _lpDisplayTable_
  
> [in] A pointer to the display table that describes the controls to appear on the property sheet.
    
 _lpConfigData_
  
> [in] A pointer to the [IMAPIProp](imapipropiunknown.md) implementation to be used for accessing the configuration properties to be displayed on the property sheet. 
    
 _ulTopPage_
  
> [in] A zero-based index to the default top page of the property sheet.
    
## Return value

S_OK 
  
> The configuration property sheet was displayed.
    
## Remarks

The **IMAPISupport::DoConfigPropsheet** method is implemented for all support objects. **DoConfigPropSheet** provides a standard user interface for displaying the properties of service providers and message services. You should use this standard dialog box for all configuration property displays so that users benefit from a consistent Windows interface. 
  
Service providers call **DoConfigPropSheet** as part of their implementation of the [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method or from a button used to display details on properties. Message services call **DoConfigPropSheet** from their message service entry point function. 
  
## Notes to callers

You can create the display table pointed to by the  _lpDisplayTable_ parameter by calling the [BuildDisplayTable](builddisplaytable.md) function or with custom code. 
  
## See also



[BuildDisplayTable](builddisplaytable.md)
  
[CreateIProp](createiprop.md)
  
[IABProvider::Logon](iabprovider-logon.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)
  
[IMSProvider::Logon](imsprovider-logon.md)
  
[IXPProvider::TransportLogon](ixpprovider-transportlogon.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

