---
title: "IMAPIStatusSettingsDialog"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIStatus.SettingsDialog
api_type:
- COM
ms.assetid: e931246e-7fff-4116-a9fc-f685988e21e8
description: "Last modified: July 23, 2011"
---

# IMAPIStatus::SettingsDialog

  
  
**Applies to**: Outlook 
  
Displays a property sheet that enables the user to change a service provider's configuration This method is not supported in status objects that MAPI implements.
  
```cpp
HRESULT SettingsDialog(
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the configuration property sheet.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the display of the property sheet. The following flag can be set:
    
UI_READONLY 
  
> Suggests that the provider should not enable users to change configuration properties. This flag is only a suggestion; it can be ignored.
    
## Return value

S_OK 
  
> The configuration property sheet was displayed successfully.
    
MAPI_E_NO_SUPPORT 
  
> The status object does not support this method, as indicated by the absence of the STATUS_SETTINGS_DIALOG flag in the **PR_RESOURCE_METHODS** ([PidTagResourceMethods](pidtagresourcemethods-canonical-property.md)) property.
    
## Remarks

The **IMAPIStatus::SettingsDialog** method displays a configuration property sheet. All service providers should support the **SettingsDialog** method, but it is not required. Service providers can implement their own property sheets or use the implementation supplied in the support object's [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) method. **DoConfigPropsheet** builds a read/write property sheet. 
  
## Notes to Implementers

If a remote transport provider has any settings, it should do the following:
  
- Open the transport provider's profile section.
    
- Get the transport provider's property settings from the profile.
    
- Display the property settings in a dialog box.
    
- If the dialog box allows editing of the property settings, check that the new settings are valid and store them back in the transport provider's profile section.
    
- Return S_OK, or any error values returned during the preceding steps.
    
## Notes to Callers

You can use the property sheet displayed through **SettingsDialog** to perform a variety of tasks, such as the following: 
  
- Specify a default message store.
    
- Specify a transport order.
    
- Specify a default address book container for browsing.
    
- Specify a search order for resolving ambiguous names.
    
- Specify a default personal address book.
    
Service providers can implement property sheets that are read/write, read-only, or a mixture of permissions, depending on the property. Service providers can implement different permissions on individual properties by setting property restrictions. The default mode for property sheets is read/write. You can request read-only property sheets by setting the UI_READONLY flag in your calls to **SettingsDialog**. Service providers that are able to implement read-only property sheets can do so. However, because some service providers cannot override the default mode, you must be prepared to handle property sheets of either type. 
  
Because a user interface is always involved in this operation, only interactive clients should call **SettingsDialog**.
  
## See also

#### Reference

[IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md)
  
[PidTagResourceMethods Canonical Property](pidtagresourcemethods-canonical-property.md)
  
[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)

