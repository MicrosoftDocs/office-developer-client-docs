---
title: "ACCELERATEABSDI"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ACCELERATEABSDI
api_type:
- HeaderDef
ms.assetid: da67dcf4-1411-4fc9-992c-115485019bd3
description: "Last modified: March 09, 2015"
---

# ACCELERATEABSDI

**Applies to**: Outlook 2013 | Outlook 2016
  
Defines a callback function to process accelerator keys in a modeless address book dialog box.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Defined function implemented by:  <br/> |MAPI  <br/> |
|Defined function called by:  <br/> |Client applications  <br/> |

```cpp
BOOL (STDMETHODCALLTYPE ACCELERATEABSDI)( 
  ULONG_PTR ulUIParam,
  LPVOID lpvmsg
);
```

## Parameters

 _ulUIParam_
  
> [in] An implementation-specific value used for passing user interface information to a function. In applications running on Microsoft Windows, _ulUIParam_ is the parent window handle for a dialog box and is of type HWND, cast to a **ULONG_PTR**. A value of zero indicates there is no parent window.

 _lpvmsg_
  
> [in] Pointer to a Windows message.

## Return value

A function with the **ACCELERATEABSDI** prototype returns TRUE if it handles the message.
  
## Remarks

A function based on the **ACCELERATEABSDI** prototype is used only with a modeless dialog, that is, only if the client application has set the DIALOG_SDI flag in the _ulFlags_ member of the [ADRPARM](adrparm.md) structure.
  
A modeless dialog shares the client application's Windows message loop, instead of having its own loop. The application, which controls the message loop, does not know what accelerator keys the dialog uses, so it calls an **ACCELERATEABSDI** based function to test for and act upon accelerator keys such as CTRL+P for printing.
  
A client's message loop calls the **ACCELERATEABSDI** based function when the client invokes a modeless address book dialog box with the [IAddrBook::Address](iaddrbook-address.md) method. This call is terminated when MAPI calls a function based on the [DISMISSMODELESS](dismissmodeless.md) function prototype.
  