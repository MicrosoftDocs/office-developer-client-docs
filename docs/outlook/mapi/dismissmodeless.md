---
title: "DISMISSMODELESS"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DISMISSMODELESS
api_type:
- COM
ms.assetid: ef93ef3d-c159-40ae-9b8d-0af8a0567565
description: "Last modified: March 09, 2015"
---

# DISMISSMODELESS

  
  
**Applies to**: Outlook 
  
Defines a callback function that MAPI calls when it has dismissed a modeless address book dialog box. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Defined function implemented by:  <br/> |Client applications  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```cpp
void (STDMETHODCALLTYPE DISMISSMODELESS)(
  ULONG_PTR ulUIParam,
  LPVOID lpvContext
);
```

## Parameters

 _ulUIParam_
  
> [in] An implementation-specific value typically used for passing user interface information to a function. For example, in Microsoft Windows this parameter is the parent window handle for the dialog box and is of type HWND, cast to a **ULONG_PTR**. A value of zero indicates there is no parent window. 
    
 _lpvContext_
  
> [in] Pointer to an arbitrary value passed to the callback function when MAPI calls it. This value can represent an address of significance to the client application. Typically, for C++ code,  _lpvContext_ is a pointer to the address of a C++ object instance. 
    
## Return value

None
  
## Remarks

When the client application invokes a modeless address book dialog box, it includes in its Windows message loop a call to a function based on the [ACCELERATEABSDI](accelerateabsdi.md) prototype, which checks for and processes accelerator keys. When the dialog box is closed, MAPI calls the **DISMISSMODELESS** based function so that the client application will stop calling the **ACCELERATEABSDI** based function. 
  
## See also



[ADRPARM](adrparm.md)

