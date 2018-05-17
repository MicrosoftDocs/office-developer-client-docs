---
title: "IMAPIFormGetViewContext"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIForm.GetViewContext
api_type:
- COM
ms.assetid: c6938986-a9f9-4ef4-9655-ded55b7357db
description: "Last modified: March 09, 2015"
---

# IMAPIForm::GetViewContext

  
  
**Applies to**: Outlook 
  
Returns the current view context for the form. 
  
```
HRESULT GetViewContext(
  LPMAPIVIEWCONTEXT FAR * ppViewContext
);
```

## Parameters

 _ppViewContext_
  
> [out] A pointer to a pointer to the form's view context.
    
## Return value

S_OK 
  
> The form's current view context was successfully returned. 
    
S_FALSE 
  
> There is no view context for the form.
    
## Remarks

Form viewers call **GetViewContext** to obtain a pointer to the view context established in a previous call to [IMAPIForm::SetViewContext](imapiform-setviewcontext.md). If no prior call has been made to **SetViewContext**, **GetViewContext** sets  _ppViewContext_ to NULL. 
  
## Notes to Implementers

Copy your form's view context pointer into the pointer passed in by the calling form viewer in the  _ppViewContext_ parameter. If the form does not have a view context, set  _ppViewContext_ to NULL. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |OpenMessageNonModal  <br/> |MFCMAPI uses the **IMAPIForm::GetViewContext** method to check whether a form has a view context.  <br/> |
   
## See also

#### Reference

[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)
  
[IMAPIForm : IUnknown](imapiformiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

