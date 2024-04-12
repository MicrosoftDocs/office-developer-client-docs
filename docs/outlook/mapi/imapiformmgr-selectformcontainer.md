---
title: "IMAPIFormMgrSelectFormContainer"
description: "IMAPIFormMgrSelectFormContainer presents a dialog box that enables the user to select a form container, and returns an interface for the container object."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIFolder.CopyMessages
api_type:
- COM
ms.assetid: c33daad6-52c4-4968-ac56-415178c9bf12
---

# IMAPIFormMgr::SelectFormContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Presents a dialog box that enables the user to select a form container, and returns an interface for the container object the user selected.
  
```cpp
HRESULT SelectFormContainer(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPMAPIFORMCONTAINER FAR * lppfcnt
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the displayed dialog box. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the form library is selected (that is, how the form container is selected). The following flags can be set:
    
MAPIFORM_SELECT_ALL_REGISTRIES 
  
> Selection can be made from all containers. This is the default selection type. 
    
MAPIFORM_SELECT_FOLDER_REGISTRY_ONLY 
  
> Selection can be made only from folder containers.
    
MAPIFORM_SELECT_NON_FOLDER_REGISTRY_ONLY 
  
> Selection can be made only from containers that are not associated with folders.
    
 _lppfcnt_
  
> [out] A pointer to a pointer to the returned interface. This interface is for the container object that is selected by the user.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form viewers typically call the **IMAPIFormMgr::SelectFormContainer** method to select a form container into which a form is installed. **SelectFormContainer** cannot be used to select the local form container, which has the value HFRMREG_LOCAL. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnSelectFormContainer  <br/> |MFCMAPI uses the **IMAPIFormMgr::SelectFormContainer** method to select a form container before rendering its contents. |
   
## See also



[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

