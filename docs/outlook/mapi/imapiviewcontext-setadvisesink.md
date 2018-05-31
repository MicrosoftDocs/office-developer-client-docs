---
title: "IMAPIViewContextSetAdviseSink"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewContext.SetAdviseSink
api_type:
- COM
ms.assetid: 4799084a-b5d1-48c3-a889-b2f0e9d68c30
description: "Last modified: March 09, 2015"
---

# IMAPIViewContext::SetAdviseSink

  
  
**Applies to**: Outlook 
  
Manages a form's registration to receive notifications about changes in the viewer. 
  
```cpp
HRESULT SetAdviseSink(
LPMAPIFORMADVISESINK pmvns
);
```

## Parameters

 _pmvns_
  
> [in] Pointer to a form advise sink object or NULL.
    
## Return value

S_OK 
  
> The registration or cancellation for form notification succeeded.
    
## Remarks

Form objects call the **IMAPIViewContext::SetAdviseSink** method to either register to learn about changes in the form viewer or cancel a prior registration. When  _pmvns_ is set to NULL, the form wants to cancel a registration. When  _pmvns_ points to a valid form advise sink, the form wants to register for future notifications. 
  
## Notes to implementers

When **SetAdviseSink** includes a form advise sink pointer, keep a reference to it until another **SetAdviseSink** call is made to cancel notification. Send a notification when a change occurs in your viewer and when you are loading a new message. 
  
For more information, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::SetAdviseSink  <br/> |MFCMAPI implements the **IMAPIViewContext::SetAdviseSink** method in this function.  <br/> |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

