---
title: "IMAPIFormMgrPrepareForm"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.PrepareForm
api_type:
- COM
ms.assetid: 8f8ee2cb-1c2a-4958-b01e-2f4aab689f89
description: "Last modified: July 23, 2011"
---

# IMAPIFormMgr::PrepareForm

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Downloads a form for opening.
  
```cpp
HRESULT PrepareForm(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPMAPIFORMINFO pfrmiInfo
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator that is displayed while the form is downloaded. The  _ulUIParam_ parameter is ignored unless the MAPI_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the form is downloaded. The following flag can be set:
    
MAPI_DIALOG 
  
> Displays a user interface to provide status or prompt the user for more information. If this flag is not set, no user interface is displayed.
    
 _pfrmiInfo_
  
> [in] A pointer to a form information object for the form to be downloaded.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Form viewers call the **IMAPIFormMgr::PrepareForm** method to download a form from a form container for opening. Most form viewers do not need to call **PrepareForm**, because both the [IMAPIFormMgr::CreateForm](imapiformmgr-createform.md) and [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md) methods call **PrepareForm**, if necessary. 
  
You can use **PrepareForm** to obtain the dynamic-link libraries (DLLs) and other files associated with a form to modify them. If the modified form is loaded back into its form container, it must be reinstalled. 
  
## See also



[IMAPIFormMgr::CreateForm](imapiformmgr-createform.md)
  
[IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

