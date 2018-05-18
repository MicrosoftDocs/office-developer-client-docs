---
title: "IMAPIFormDoVerb"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIForm.DoVerb
api_type:
- COM
ms.assetid: 8b582571-b448-4476-91d9-4cc94dbec710
description: "Last modified: March 09, 2015"
---

# IMAPIForm::DoVerb

  
  
**Applies to**: Outlook 
  
Requests that the form perform whatever tasks it associates with a specific verb.
  
```cpp
HRESULT DoVerb(
  LONG iVerb,
  LPMAPIVIEWCONTEXT lpViewContext,
  ULONG_PTR hwndParent,
  LPCRECT lprcPosRect
);
```

## Parameters

 _iVerb_
  
> [in] The number associated with one of the form's verbs.
    
 _lpViewContext_
  
> [in] A pointer to a view context object. The  _lpViewContext_ parameter can be **null**.
    
 _hwndParent_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays. The  _hwndParent_ parameter should be **null** if the dialog box or window is not modal. 
    
 _lprcPosRect_
  
> [in] A pointer to a Win32 [RECT](http://msdn.microsoft.com/en-us/library/dd162897%28VS.85%29.aspx) structure that contains the size and position of the form's window. 
    
## Return value

S_OK 
  
> The verb was successfully invoked.
    
OLEOBJ_S_CANNOT_DOVERB_NOW 
  
> The verb represented by the  _iVerb_ parameter is valid, but the form cannot perform the operations currently associated with it. 
    
## Remarks

Form viewers call the **IMAPIForm::DoVerb** method to request that the form perform the tasks that it associates with each verb that the form supports. 
  
Each of the supported verbs is identified by a numeric value, passed to **DoVerb** in the  _iVerb_ parameter. Typical implementations of **DoVerb** contain a **switch** statement that tests the values that are valid for the  _iVerb_ parameter for the form. 
  
## Notes to Implementers

If the form viewer specifies a view context in the  _lpViewContext_ parameter, use it in your **DoVerb** implementation instead of the view context passed in an earlier call to the [IMAPIForm::SetViewContext](imapiform-setviewcontext.md) method. Make whatever changes are necessary to your internal data structures and do not save the view context. 
  
Perform the following tasks in your **DoVerb** implementation: 
  
- Execute whatever code is necessary for the particular verb that is associated with the  _iVerb_ parameter. 
    
- If necessary, restore the original view context.
    
- If an unknown verb number was passed in, return MAPI_E_NO_SUPPORT. Otherwise, return a result based on the success or failure of whatever verb was executed.
    
- Close the form. It is always your responsibility to close the form after a **DoVerb** call completes. 
    
Some verbs, such as Print, should be modal with respect to the **DoVerb** call — that is, the indicated operation must be finished before the **DoVerb** call returns. 
  
To obtain the **RECT** structure used by a form's window, call the [GetWindowRect](http://msdn.microsoft.com/en-us/library/ms633519) function. 
  
Do not save the handle in the  _hwndParent_ parameter because, although it usually remains valid until the completion of **DoVerb**, it can be destroyed immediately upon the call's return.
  
## Notes to Callers

You can make non-modal verbs act as modal verbs by pointing  _lpViewContext_ to a view context implementation that returns the VCSTATUS_MODAL flag from its [IMAPIViewContext::GetViewStatus](imapiviewcontext-getviewstatus.md) method. 
  
For more information about verbs in MAPI, see [Form Verbs](form-verbs.md). For more information about how verbs are handled in OLE, see [OLE and Data Transfer](http://msdn.microsoft.com/en-us/library/ms693425%28VS.85%29.aspx).
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::CallDoVerb  <br/> |MFCMAPI uses the **IMAPIForm::DoVerb** method to invoke a verb on a form.  <br/> |
   
## See also

#### Reference

[IMAPIForm::SetViewContext](imapiform-setviewcontext.md)
  
[IMAPIViewContext::GetViewStatus](imapiviewcontext-getviewstatus.md)
  
[IMAPIForm : IUnknown](imapiformiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Form Verbs](form-verbs.md)

