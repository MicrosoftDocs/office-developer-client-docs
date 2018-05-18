---
title: "IMAPISupportDetails"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.Details
api_type:
- COM
ms.assetid: 1a62efa2-dd6b-4acb-a760-defa601c20c9
description: "Last modified: July 23, 2011"
---

# IMAPISupport::Details

  
  
**Applies to**: Outlook 
  
Displays a dialog box that shows details about a particular address book entry.
  
```cpp
HRESULT Details(
  ULONG_PTR FAR * lpulUIParam,
  LPFNDISMISS lpfnDismiss,
  LPVOID lpvDismissContext,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPFNBUTTON lpfButtonCallback,
  LPVOID lpvButtonContext,
  LPSTR lpszButtonText,
  ULONG ulFlags
);
```

## Parameters

 _lpulUIParam_
  
> [out] A pointer to the handle to the parent window of the returned dialog box.
    
 _lpfnDismiss_
  
> [in] A pointer to a function based on the [DISMISSMODELESS](dismissmodeless.md) prototype, or NULL. This member applies only to the modeless version of the dialog box, as indicated by the DIALOG_SDI flag being set. MAPI calls the **DISMISSMODELESS** function when the user dismisses the modeless address dialog box, informing a client that is calling **IMAPISupport::Details** that the dialog box is no longer active. 
    
 _lpvDismissContext_
  
> [in] A pointer to context information to pass to the **DISMISSMODELESS** function pointed to by the  _lpfnDismiss_ parameter. This parameter applies only to the modeless version of the dialog box, by including the DIALOG_SDI flag in the  _ulFlags_ parameter. 
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for which details are displayed.
    
 _lpfButtonCallback_
  
> [in] A pointer to a function based on the [LPFNBUTTON](lpfnbutton.md) function prototype. An **LPFNBUTTON** function adds a button to the details dialog box. 
    
 _lpvButtonContext_
  
> [in] A pointer to data used as a parameter for the function specified by the  _lpfButtonCallback_ parameter. 
    
 _lpszButtonText_
  
> [in] A pointer to a string that contains text to be applied to the added button if that button is extensible. The  _lpszButtonText_ parameter should be NULL if an extensible button is not needed. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text for the  _lpszButtonText_ parameter. The following flag can be set: 
    
DIALOG_MODAL
  
> Display the modal version of the common address dialog box. This flag is mutually exclusive with DIALOG_SDI.
    
DIALOG_SDI
  
>  Display the modeless version of the common address dialog box. This flag is mutually exclusive with DIALOG_MODAL. 
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
## Return value

S_OK 
  
> The details dialog box was successfully displayed for the address book entry.
    
## Remarks

The **IMAPISupport::Details** method is implemented for address book provider support objects. Address book providers call **Details** to display a dialog box that gives details on a particular entry in the address book. The  _lpfButtonCallback_,  _lpvButtonContext_, and  _lpszButtonText_ parameters can be used to add a client-defined button to the dialog box. When the button is clicked, MAPI calls the callback function pointed to by  _lpfButtonCallback_, passing both the entry identifier of the button and the data in  _lpvButtonContext_. If an extensible button is not needed,  _lpszButtonText_ should be NULL. 
  
## See also

#### Reference

[ADRPARM](adrparm.md)
  
[IMAPISupport::Address](imapisupport-address.md)
  
[LPFNBUTTON](lpfnbutton.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

