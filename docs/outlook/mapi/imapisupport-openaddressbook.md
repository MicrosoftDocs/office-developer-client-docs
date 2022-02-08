---
title: "IMAPISupportOpenAddressBook"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.OpenAddressBook
api_type:
- COM
ms.assetid: d8da8be1-3efe-410a-bcce-49e522602d80
description: "Last modified: July 23, 2011"
---

# IMAPISupport::OpenAddressBook

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the address book.
  
```cpp
HRESULT OpenAddressBook(
LPCIID lpInterface,
ULONG ulFlags,
LPADRBOOK FAR * lppAdrBook
);
```

## Parameters

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the address book. Valid values are NULL, which indicates the standard address book interface [IAddrBook](iaddrbookimapiprop.md), and IID_IAddrBook.
    
 _ulFlags_
  
> Reserved; must be zero.
    
 _lppAdrBook_
  
> [out] A pointer to a pointer to the address book.
    
## Return value

S_OK 
  
> Access to the address book was provided.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded, but one or more address book providers could not be loaded. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPISupport::OpenAddressBook** method is implemented for all service provider support objects. Service providers, typically tightly coupled message store and transport providers, call **OpenAddressBook** to get access to the address book. The returned **IAddrBook** pointer can be used for a variety of address book tasks, including opening address book containers, finding messaging users, and displaying address dialog boxes. 
  
## Notes to callers

 **OpenAddressBook** can return MAPI_W_ERRORS_RETURNED if it cannot load one or more of the address book providers in the current profile. This value is a warning and you should treat the call as successful. Even if all of the address book providers failed to load, **OpenAddressBook** still succeeds, returning MAPI_W_ERRORS_RETURNED and an **IAddrBook** pointer in the _lppAdrBook_ parameter. Because **OpenAddressBook** always returns a valid **IAddrBook** pointer, you must release it when you are finished using it. 
  
If one or more address book providers failed to load, call [IMAPISupport::GetLastError](imapisupport-getlasterror.md) to obtain a [MAPIERROR](mapierror.md) structure that contains information about the providers that did not load. 
  
## See also



[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)
  
[IMAPISession::OpenAddressBook](imapisession-openaddressbook.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

