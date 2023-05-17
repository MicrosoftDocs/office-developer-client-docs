---
title: "IMAPIFormShutdownForm"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIForm.ShutdownForm
api_type:
- COM
ms.assetid: f1e2a526-40ad-4a93-908f-8ab9a65928a8
---

# IMAPIForm::ShutdownForm

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Closes the form.
  
```cpp
HRESULT ShutdownForm(
  ULONG ulSaveOptions
);
```

## Parameters

 _ulSaveOptions_
  
> [in] A value that controls how or whether data in the form is saved before the form is closed. One of the following flags can be set:
    
SAVEOPTS_NOSAVE 
  
> Form data should not be saved.
    
SAVEOPTS_PROMPTSAVE 
  
> The user should be prompted to save any changed data in the form.
    
SAVEOPTS_SAVEIFDIRTY 
  
> Form data should be saved if it has changed since the last save. If no user interface is being displayed, the form can optionally switch to using the functionality for the SAVEOPTS_NOSAVE option.
    
## Return value

S_OK 
  
> The form was closed.
    
E_UNEXPECTED 
  
> The form was already closed by a prior call to **ShutdownForm**.
    
## Remarks

Form viewers call the **IMAPIForm::ShutdownForm** method to close a form. 
  
## Notes to implementers

Perform the following tasks in your implementation of **ShutdownForm**:
  
1. Check that a viewer has not already called **ShutdownForm**, and return E_UNEXPECTED if it has. Although this is unlikely, you should check.
    
2. Call your form's [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28VS.85%29.aspx) method so that storage for the form and any internal data structures remain available until processing is finished. 
    
3. Determine whether there are any unsaved changes to the form's data. Save unsaved data according to how the  _ulSaveOptions_ parameter is set by calling your viewer's [IMAPIMessageSite::SaveMessage](imapimessagesite-savemessage.md) method. 
    
4. Destroy your form's user interface window.
    
5. Release your form's message and message site objects by calling their [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) methods. 
    
6. Notify all registered viewers of the pending shutdown by calling their [IMAPIViewAdviseSink::OnShutdown](imapiviewadvisesink-onshutdown.md) methods. 
    
7. Call the [IMAPIViewContext::SetAdviseSink](imapiviewcontext-setadvisesink.md) method to cancel your form's registration for notification by setting the advise sink pointer to **null**.
    
8. Call the [MAPIFreeBuffer](mapifreebuffer.md) function to free the memory for your form's properties. 
    
9. Call your form's **IUnknown::Release** method, matching the **AddRef** call made in step 2. 
    
10. Return S_OK.
    
> [!NOTE]
> After these actions have been completed, the only valid methods on the form object that may be called are those from the [IUnknown](https://msdn.microsoft.com/library/ms680509%28v=VS.85%29.aspx) interface. 
  
## Notes to callers

When **ShutdownForm** returns, regardless of whether it returns an error, release the form by calling its **IUnknown::Release** method. You can safely ignore any errors returned by **ShutdownForm**.
  
## See also



[IMAPIMessageSite::SaveMessage](imapimessagesite-savemessage.md)
  
[IMAPIViewAdviseSink::OnShutdown](imapiviewadvisesink-onshutdown.md)
  
[IMAPIViewContext::SetAdviseSink](imapiviewcontext-setadvisesink.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPIForm : IUnknown](imapiformiunknown.md)

