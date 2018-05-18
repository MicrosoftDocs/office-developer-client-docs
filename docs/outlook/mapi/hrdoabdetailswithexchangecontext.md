---
title: "HrDoABDetailsWithExchangeContext"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b4e7fed2-88e4-4e14-90b6-913a1b7e338a
description: "Last modified: March 09, 2015"
---

# HrDoABDetailsWithExchangeContext

  
  
**Applies to**: Outlook 
  
Ensures that the **OpenEntry** method is opened by the expected Exchange address book provider. This function works similarly to [IAddrBook::Details](iaddrbook-details.md), but opens the **entryID** using the Exchange address book identified by the  _pEmsmdbUID_ parameter. 
  
|||
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrOpenABEntryWithExchangeContext(
  LPMAPISESSION   pmsess,
  const MAPIUID  *pEmsmdbUID,
  LPADRBOOK pAddrBook,
  ULONG_PTR FAR * lpulUIParam,
  LPFNDISMISS lpfnDismiss,
  LPVOID lpvDismissContext,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPENTRYID lpEntryID,
  LPFNBUTTON lpfButtonCallback,
  LPVOID lpvButtonContext,
  LPSTR lpszButtonText,
  ULONG ulFlags,
);
```

## Parameters

 _pmsess_
  
> The logged on **IMAPISession**. It cannot be NULL.
    
 _pEmsmdbUID_
  
> A pointer to an **emsmdbUID** that identifies the Exchange Service that contains the Exchange address book provider that is used by the function to open the entry identifier. If the incoming entry identifier is not an Exchange address book provider entry identifier, this parameter is ignored and the function behaves like [IAddrBook::OpenEntry](iaddrbook-openentry.md). If this parameter is NULL or a zero **MAPIUID**, this function also acts exactly like [IAddrBook::OpenEntry](iaddrbook-openentry.md). 
    
 _pAddrBook_
  
> [in] The address book used to open the entry identifier. It cannot be NULL.
    
 _lpulUIParam_
  
> [out] A handle to the parent window for the dialog box.
    
 _lpfnDismiss_
  
> [in] A pointer to a function based on the **DISMISSMODELESS** prototype, or NULL. This member applies only to the modeless version of the dialog box, as indicated by the DIALOG_SDI flag being set. MAPI calls the **DISMISSMODELESS** function when the user dismisses the modeless address dialog box, informing a client that is calling Details that the dialog box is no longer active. 
    
 _lpvDismissContext_
  
> [in] A pointer to context information to pass to the **DISMISSMODELESS** function pointed to by the  _lpfnDismiss_ parameter. This parameter applies only to the modeless version of the dialog box by including the **DIALOG_SDI** flag in the  _ulFlags_ parameter. 
    
 _cbEntryID_
  
> [in] The byte count of the entry identifier specified by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier that represents the address book entry to open.
    
 _lpfButtonCallback_
  
> [in] A pointer to a function based on the **LPFNBUTTON** function prototype. An **LPFNBUTTON** function adds a button to the details dialog box. 
    
 _lpvButtonContext_
  
> [in] A pointer to data that was used as a parameter for the function specified by the  _lpfButtonCallback_ parameter. 
    
 _lpszButtonText_
  
> [in] A pointer to a string that contains text to be applied to the added button, if that button is extensible. The  _lpszButtonText_ parameter should be NULL when an extensible button is not needed. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text for the  _lpszButtonText_ parameter. The following flags can be set: 
    
AB_TELL_DETAILS_CHANGE
  
> Indicates that Details returns TRUE if changes are actually made to the address; otherwise, Details returns FALSE.
    
DIALOG_MODAL
  
> Displays the modal version of the common address dialog box. This flag is mutually exclusive with DIALOG_SDI.
    
DIALOG_SDI
  
> Displays the modeless version of the common address dialog box. This flag is mutually exclusive with DIALOG_MODAL.
    
MAPI_UNICODE
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    

