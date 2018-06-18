---
title: "LPFNBUTTON"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.LPFNBUTTON
api_type:
- COM
ms.assetid: cb91ae1d-1ea8-4f02-a1f1-f2a356a71477
description: "Last modified: March 09, 2015"
---

# LPFNBUTTON

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Defines a callback function that MAPI calls to activate an optional button control in an address book dialog box. This button is typically a **Details** button. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Defined function implemented by:  <br/> |Service providers  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```cpp
SCODE (STDMETHODCALLTYPE FAR * LPFNBUTTON)(
  ULONG_PTR ulUIParam,
  LPVOID lpvContext,
  ULONG cbEntryID,
  LPENTRYID lpSelection,
  ULONG ulFlags
);
```

## Parameters

 _ulUIParam_
  
> [in] Handle of the parent windows for any dialog boxes or windows this function displays.
    
 _lpvContext_
  
> [in] Pointer to an arbitrary value passed to the callback function when MAPI calls it. This value can represent an address of significance to the client application. Typically, for C++ code,  _lpvContext_ represents a pointer to a C++ object. 
    
 _cbEntryID_
  
> [in] Size, in bytes, of the entry identifier pointed to by the  _lpSelection_ parameter. 
    
 _lpSelection_
  
> [in] Pointer to the entry identifier defining the selection in the dialog box.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Client applications call a callback function based on the **LPFNBUTTON** prototype to define a button in a details dialog box. The client passes a pointer to the callback function in calls to the [IAddrBook::Details](iaddrbook-details.md) method. 
  
Service providers call a hook function based on the **LPFNBUTTON** prototype to define a button in a details dialog box. The provider passes a pointer to this hook function in calls to the [IMAPISupport::Details](imapisupport-details.md) method. 
  
In both cases, when the dialog box is displayed and the user chooses the defined button, MAPI calls **LPFNBUTTON**. 
  
## See also



[BuildDisplayTable](builddisplaytable.md)

