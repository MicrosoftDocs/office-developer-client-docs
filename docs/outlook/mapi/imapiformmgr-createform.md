---
title: "IMAPIFormMgrCreateForm"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.CreateForm
api_type:
- COM
ms.assetid: 7d4d50f8-3904-4e93-a535-ac7decceb1a3
description: "Last modified: March 09, 2015"
---

# IMAPIFormMgr::CreateForm

  
  
**Applies to**: Outlook 
  
Opens a form to create a new message based on the form's message class.
  
```cpp
HRESULT CreateForm(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  IMAPIFormInfo pfrminfoToActivate,
  REFIID refiidToAsk,
  LPVOID FAR * ppvObj
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window for the progress indicator that is displayed while the form is opened. The  _ulUIParam_ parameter is ignored unless the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the form is opened. The following flag can be set:
    
MAPI_DIALOG 
  
> Displays a user interface to provide status or prompt the user for more information. If this flag is not set, no user interface is displayed.
    
 _pfrminfoToActivate_
  
> [in] A pointer to the form information object that is used to open the form.
    
 _refiidToAsk_
  
> [in] A pointer to the interface identifier (IID) for the interface to be returned for the form object that was created. The  _refiidToAsk_ parameter must not be NULL. 
    
 _ppvObj_
  
> [out] A pointer to a pointer to the returned interface.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_INTERFACE 
  
> The requested interface is not supported by the form object.
    
## Remarks

Form viewers call the **IMAPIFormMgr::CreateForm** method to open a form to create a new message based on the form's message class. **CreateForm** opens the form by creating an instance of the form server for that form as described in the given form information object. If required, **CreateForm** calls the [IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md) method to download the form server code to the user's disk. 
  
The  _pfrminfoToActivate_ parameter must point to a form information object that has been correctly resolved. 
  
After the form has been opened, the calling form viewer must set up a message by using the [IPersistMessage](ipersistmessageiunknown.md) interface and can optionally set up a view context for the form. For more information, see [Launching a Form Server](launching-a-form-server.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFormFunctions.cpp  <br/> |CreateAndDisplayNewMailInFolder  <br/> |MFCMAPI uses the **IMAPIFormMgr::CreateForm** method to create a form before displaying it.  <br/> |
   
## See also



[IMAPIFormMgr::PrepareForm](imapiformmgr-prepareform.md)
  
[IPersistMessage : IUnknown](ipersistmessageiunknown.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Launching a Form Server](launching-a-form-server.md)

