---
title: "IOlkAccountManagerDisplayAccountList"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: a637dcab-81e0-4195-a1d5-61d9957fcf10
description: "Displays either the Account Settings or Add New Account dialog box."
---

# IOlkAccountManager::DisplayAccountList

Displays either the **Account Settings** or **Add New Account** dialog box. 
  
## Quick info

See [IOlkAccountManager](iolkaccountmanager.md).
  
```cpp
HRESULT IOlkAccountManager::DisplayAccountList ( 
    HWND hwnd,
    DWORD dwFlags,
    LPCWSTR wszTitle,
    DWORD cCategories,
    const CLSID * rgclsidCategories,
    const CLSID * pclsidType
);

```

## Parameters

_hwnd_
  
> [in] The handle to the window to which the displayed dialog box is modal. May be zero.
    
_dwFlags_
  
> [in] Flags to modify the behavior of the display. 
    
   - **ACCTUI_NO_WARNING**—Do not display the warning that changes will not take effect until Outlook is restarted. Applies only if the application is running in-process with Outlook.exe.
    
   - **ACCTUI_SHOW_DATA_TAB**—Show the **Account Settings** dialog box with the **Data** tab selected. Valid only if **ACCTUI_SHOW_ACCTWIZARD** is not set. 
    
   - **ACCTUI_SHOW_ACCTWIZARD**—Display the **Add New Account** dialog box. 
    
_wszTitle_
  
> [in] This parameter is not used and should be NULL.
    
_cCategories_
  
> [in] This parameter is not used and must be NULL. 
    
_rgclsidCategories_
  
> [in] This parameter is not used and must be NULL.
    
_pclsidType_
  
> [in] This parameter is not used and must be NULL.
    
## Return values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call was successful.  <br/> |
|E_ACCT_UI_BUSY  <br/> |The dialog box could not be created.  <br/> |
|E_OLK_NOT_INITIALIZED  <br/> |The account manager has not been initialized for use.  <br/> |
|MAPI_E_CALL_FAILED  <br/> |The **Add New Account** dialog box returned an error.  <br/> |
|MAPI_E_INVALID_PARAMETER  <br/> |The  _cCategories_,  _rgclsidCategories_, or  _pclsidType_ parameter is non-NULL.  <br/> |
|MAPI_E_USER_CANCEL  <br/> |The **Account Settings** dialog box returned an error.  <br/> |
   
## Remarks

The  _cCategories_,  _rgclsidCategories_, and  _pclsidType_ parameters are not used at this time and must be NULL.  _wszTitle_ is not used and should also be NULL. 
  

