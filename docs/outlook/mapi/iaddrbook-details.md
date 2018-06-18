---
title: "IAddrBookDetails"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.Details
api_type:
- COM
ms.assetid: 4eee4382-98c3-4714-8920-8d72edef00b8
description: "Last modified: March 09, 2015"
---

# IAddrBook::Details

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
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
  
> [in] A pointer to a handle of the parent window for the dialog box.
    
 _lpfnDismiss_
  
> [in] A pointer to a function based on the [DISMISSMODELESS](dismissmodeless.md) prototype, or NULL. This member applies only to the modeless version of the dialog box, as indicated by the DIALOG_SDI flag being set. MAPI calls the **DISMISSMODELESS** function when the user dismisses the modeless address dialog box, informing a client that is calling **Details** that the dialog box is no longer active. 
    
 _lpvDismissContext_
  
> [in] A pointer to context information to pass to the **DISMISSMODELESS** function pointed to by the  _lpfnDismiss_ parameter. This parameter applies only to the modeless version of the dialog box, by including the DIALOG_SDI flag in the  _ulFlags_ parameter. 
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for the entry for which details are displayed.
    
 _lpfButtonCallback_
  
> [in] A pointer to a function based on the [LPFNBUTTON](lpfnbutton.md) function prototype. An **LPFNBUTTON** function adds a button to the details dialog box. 
    
 _lpvButtonContext_
  
> [in] A pointer to data that was used as a parameter for the function specified by the  _lpfButtonCallback_ parameter. 
    
 _lpszButtonText_
  
> [in] A pointer to a string that contains text to be applied to the added button, if that button is extensible. The  _lpszButtonText_ parameter should be NULL if you do not need an extensible button. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text for the  _lpszButtonText_ parameter. The following flags can be set: 
    
AB_TELL_DETAILS_CHANGE
  
> Indicates that **Details** returns S_OK if changes are actually made to the address; otherwise, **Details** returns S_FALSE. 
    
DIALOG_MODAL
  
> Display the modal version of the common address dialog box, which is always shown in non-Outlook clients. This flag is mutually exclusive with DIALOG_SDI.
    
DIALOG_SDI
  
>  Display the modeless version of the common address dialog box. This flag is ignored for non-Outlook clients. 
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
## Return value

S_OK 
  
> The details dialog box was successfully displayed for the address book entry.
    
## Remarks

Client applications call the **Details** method to display a dialog box that provides details about a particular entry in the address book. You can use the  _lpfButtonCallback_,  _lpvButtonContext_, and  _lpszButtonText_ parameters to add a client-defined button to the dialog box. When the button is clicked, MAPI calls the callback function pointed to by  _lpfButtonCallback_, passing both the entry identifier of the button and the data in  _lpvButtonContext_. If you do not need an extensible button,  _lpszButtonText_ should be NULL. 
  
 **Details** supports Unicode character strings; Unicode strings are converted to the multibyte character string (MBCS) format before they are displayed in the details dialog box. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|BaseDialog.cpp  <br/> |CBaseDialog::OnOpenEntryID  <br/> |MFCMAPI uses the **Details** method to display a dialog box that shows the details for an address book entry.  <br/> |
   
## See also



[ADRPARM](adrparm.md)
  
[IAddrBook::Address](iaddrbook-address.md)
  
[LPFNBUTTON](lpfnbutton.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

