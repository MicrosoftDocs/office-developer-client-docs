---
title: "IMAPIFormMgrOpenFormContainer"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.OpenFormContainer
api_type:
- COM
ms.assetid: df02bdc5-903a-4ce2-9f43-5f4513ea19b3
description: "Last modified: March 09, 2015"
---

# IMAPIFormMgr::OpenFormContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens an [IMAPIFormContainer](imapiformcontaineriunknown.md) interface for a specific form container. 
  
```cpp
HRESULT OpenFormContainer(
  HFRMREG hfrmreg,
  LPUNKNOWN lpunk,
  LPMAPIFORMCONTAINER FAR * lppfcnt
);
```

## Parameters

 _hfrmreg_
  
> [in] An HFRMREG enumeration that indicates the form library to open (that is, the form container to open). An HFRMREG enumeration is an enumeration that is specific to a form library provider. Possible HFRMREG values include the following:
    
HFRMREG_DEFAULT 
  
> A convenient form container.
    
HFRMREG_FOLDER 
  
> A folder container. 
    
HFRMREG_PERSONAL 
  
> The container for the default message store. 
    
HFRMREG_LOCAL 
  
> A local form container. 
    
 _lpunk_
  
> [in] A pointer to the object for which the interface is opened. The  _lpunk_ parameter must be **null** unless the value for the  _hfrmreg_ parameter requires an object pointer. 
    
 _lppfcnt_
  
> [out] A pointer to a pointer to the returned form container object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_INTERFACE 
  
> The object pointed to by  _lpunk_ does not support the required interface. 
    
## Remarks

Form viewers call the **IMAPIFormMgr::OpenFormContainer** method to open an **IMAPIFormContainer** interface for a specific form container. This interface can then be used for installing forms into and removing forms from a form container. 
  
## Notes to callers

If the value in  _hfrmreg_ is HFRMREG_FOLDER, the interface identifier used in  _lpunk_ must be non- **null** and must allow [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) method calls to an [IMAPIFolder](imapifolderimapicontainer.md) interface. 
  
To open the local form container, you must use a call to **OpenFormContainer** method or the [MAPIOpenLocalFormContainer](mapiopenlocalformcontainer.md) function; you cannot use the [IMAPIFormMgr::SelectFormContainer](imapiformmgr-selectformcontainer.md) method to enable the user to select the local form container. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnOpenFormContainer  <br/> |MFCMAPI uses the **IMAPIFormMgr::OpenFormContainer** method to retrieve a form container so the container's contents can be rendered.  <br/> |
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnOpenFormContainer  <br/> |MFCMAPI uses the **IMAPIFormMgr::OpenFormContainer** method to retrieve a form container for a folder so the container's contents can be rendered.  <br/> |
   
## See also



[IMAPIFormContainer::InstallForm](imapiformcontainer-installform.md)
  
[IMAPIFormMgr::SelectFormContainer](imapiformmgr-selectformcontainer.md)
  
[MAPIOpenLocalFormContainer](mapiopenlocalformcontainer.md)
  
[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

