---
title: "IMAPIFormContainerGetDisplay"
description: "IMAPIFormContainerGetDisplay returns the display name of a form container. This article describes its syntax, parameters, and return value."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFormContainer.GetDisplay
api_type:
- COM
ms.assetid: 6829e273-4a75-4278-b58a-ae7543e075ac
---

# IMAPIFormContainer::GetDisplay

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the display name of a form container.
  
```cpp
HRESULT GetDisplay(
  ULONG ulFlags,
  LPSTR FAR * pszDisplayName
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the returned string. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned string is in Unicode format. If the MAPI_UNICODE flag is not set, the string is in ANSI format.
    
 _pszDisplayName_
  
> [out] A pointer to a string that contains the display name of the form container.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FormContainerDlg.cpp  <br/> |CFormContainerDlg::CFormContainerDlg  <br/> |MFCMAPI uses the **IMAPIFormContainer::GetDisplay** method to get the name of the form container when it renders CFormContainerDlg. |
   
## See also



[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

