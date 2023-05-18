---
title: "IMAPIFormContainerRemoveForm"
description: "Describes the syntax, parameters, return value, and sample code of IMAPIFormContainerRemoveForm, which removes a particular form from a form container."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormContainer.RemoveForm
api_type:
- COM
ms.assetid: 7f851ce8-bd01-4ea5-86e0-e44323cc0aab
---

# IMAPIFormContainer::RemoveForm

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Removes a particular form from a form container.
  
```cpp
HRESULT RemoveForm(
  LPCSTR szMessageClass
);
```

## Parameters

 _szMessageClass_
  
> [in] A string that names the message class of the form to be removed from the form container. Message class names are always ANSI strings, never Unicode.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NOT_FOUND 
  
> The message class passed in the _szMessageClass_ parameter does not match the message class of any form in the form container. 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FormContainerDlg.cpp  <br/> |CFormContainerDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **IMAPIFormContainer::RemoveForm** method to delete a form from a form container. |
   
## See also



[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

