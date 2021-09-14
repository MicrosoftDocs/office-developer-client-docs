---
title: "IMAPISessionOpenAddressBook"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.OpenAddressBook
api_type:
- COM
ms.assetid: 2b6a4c6a-bb71-4ea1-a3b6-90a2722880fb
description: "Last modified: March 09, 2015"
---

# IMAPISession::OpenAddressBook

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens the MAPI integrated address book, returning an [IAddrBook](iaddrbookimapiprop.md) pointer for further access. 
  
```cpp
HRESULT OpenAddressBook(
  ULONG_PTR ulUIParam,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPADRBOOK FAR * lppAdrBook
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the common address dialog box and other related displays.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the address book. Passing **null** returns a pointer to the address book's standard interface, [IAddrBook : IMAPIProp](iaddrbookimapiprop.md). 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the opening of the address book. The following flag can be set:
    
AB_NO_DIALOG 
  
> Suppresses the display of dialog boxes. If the AB_NO_DIALOG flag is not set, the address book providers that contribute to the integrated address book can prompt the user for any necessary information. 
    
 _lppAdrBook_
  
> [out] A pointer to a pointer to the address book.
    
## Return value

S_OK 
  
> The address book was successfully opened.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded, but the containers of one or more address book providers could not be opened. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPISession::OpenAddressBook** method opens the MAPI integrated address book, a collection of the top-level containers of all of the address book providers in the profile. The pointer that is returned in the  _lppAdrBook_ parameter provides further access to the contents of the address book. This allows the caller to perform tasks such as opening individual containers, finding messaging users, and displaying common address dialog boxes. 
  
## Notes to callers

 **OpenAddressBook** returns MAPI_W_ERRORS_RETURNED if it cannot load one or more of the address book providers in the profile. This value is a warning, not an error value; handle it as you would S_OK. **OpenAddressBook** always returns a valid pointer in the  _lppAdrBook_ parameter, regardless of how many of the address book providers failed to load. Therefore, you must always call the address book's [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method at some point before logging off. 
  
When **OpenAddressBook** returns MAPI_W_ERRORS_RETURNED, call [IMAPISession::GetLastError](imapisession-getlasterror.md) to obtain a [MAPIERROR](mapierror.md) structure that contains information about the failing providers. A single **MAPIERROR** structure is returned that contains information supplied by all of the providers. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIObjects.cpp  <br/> |CMapiObjects::GetAddrBook  <br/> |MFCMAPI uses the **IMAPISession::OpenAddressBook** method to obtain the integrated address book.  <br/> |
   
## See also



[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)
  
[IMAPISession::GetLastError](imapisession-getlasterror.md)
  
[MAPIERROR](mapierror.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

