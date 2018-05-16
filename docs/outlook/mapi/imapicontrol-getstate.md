---
title: "IMAPIControlGetState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIControl.GetState
api_type:
- COM
ms.assetid: fb321b48-3e5f-4b99-9af0-a57b66f26a2e
description: "Last modified: July 23, 2011"
---

# IMAPIControl::GetState

  
  
**Applies to**: Outlook 
  
Retrieves a value that indicates whether the button control is enabled or disabled.
  
```
HRESULT GetState(
  ULONG ulFlags,
  ULONG FAR * lpulState
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpulState_
  
> [out] A pointer to a value that indicates the state of the button control. One of the following values can be returned:
    
MAPI_DISABLED 
  
> The button control is disabled and cannot be clicked. 
    
MAPI_ENABLED 
  
> The button control is enabled and can be clicked.
    
## Return value

S_OK 
  
> The state of the button control was successfully retrieved.
    
## Remarks

Service providers implement the **IMAPIControl::GetState** method to provide MAPI with the state of a button control. If the button is enabled, it can respond to a mouse click or key press. If it is disabled, the button appears dimmed and does not respond to a mouse click or key press. 
  
For more information about how to implement **GetState** and the other [IMAPIControl : IUnknown](imapicontroliunknown.md) methods, see [Control Object Implementation](control-object-implementation.md).
  
## See also

#### Reference

[IMAPIControl::Activate](imapicontrol-activate.md)
  
[IMAPIControl : IUnknown](imapicontroliunknown.md)

