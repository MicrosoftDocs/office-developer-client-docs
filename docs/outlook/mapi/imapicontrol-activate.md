---
title: "IMAPIControlActivate"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIControl.Activate
api_type:
- COM
ms.assetid: 2b641030-2429-4217-a648-0a9f3d1a1b29
description: "Last modified: July 23, 2011"
---

# IMAPIControl::Activate

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs a task such as displaying a dialog box or starting a programmatic operation when a client application user clicks the button control.
  
```cpp
HRESULT Activate(
  ULONG ulFlags,
  ULONG_PTR ulUIParam
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _ulUIParam_
  
> [in] A handle to the parent window of the dialog box on which the button control appears.
    
## Return value

S_OK 
  
> The button control was successfully activated.
    
## Remarks

The **IMAPIControl::Activate** method performs tasks following a user's click of the button control. After the click occurs, as part of the processing of the display table, MAPI makes a call to **Activate** after first calling [IMAPIControl::GetState](imapicontrol-getstate.md) to determine whether the button is enabled. 
  
For more information about how to implement **Activate** and the other [IMAPIControl : IUnknown](imapicontroliunknown.md) methods, see [Control Object Implementation](control-object-implementation.md).
  
## See also



[IMAPIControl::GetState](imapicontrol-getstate.md)
  
[IMAPIControl : IUnknown](imapicontroliunknown.md)

