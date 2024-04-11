---
title: "HrOpenABEntryWithSupport" 
description: This article describes the HrOpenABEntryWithSupport function and provides syntax and parameters. Do not use this function.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: eaa988ea-aee1-4066-8c78-2b6c28def5e0
---

# HrOpenABEntryWithSupport

**Applies to**: Outlook 2013 | Outlook 2016
  
Do not use this function.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |abhelp.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |

```cpp
HRESULT HrOpenABEntryWithSupport(
  LPMAPISUP lpSup,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  LPCIID  lpInterface,
  ULONG  ulFlags,
  ULONG FAR * lpulObjType,
  LPUNKNOWN FAR * lppUnk
);
```

## Parameters

 _lpSup_
  
>

 _cbEntryID_
  
> [in] The byte count of the entry identifier specified by the _lpEntryID_ parameter.

 _lpEntryID_
  
> [in] A pointer to the entry identifier that represents the address book entry to open.

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) of the interface to be used to access the open entry. Passing NULL returns the standard interface of the object. For messaging users, the standard interface is [IMailUser : IMAPIProp](imailuserimapiprop.md). For distribution lists, it is [IDistList : IMAPIContainer](idistlistimapicontainer.md), and for containers, it is [IABContainer : IMAPIContainer](iabcontainerimapicontainer.md). Callers can set _lpInterface_ to the appropriate standard interface or an interface in the inheritance hierarchy.

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text for the _lpszButtonText_ parameter. The following flags can be set:

AB_TELL_DETAILS_CHANGE
  
> Indicates that Details returns TRUE if changes are actually made to the address; otherwise, Details returns FALSE.

DIALOG_MODAL
  
> Displays the modal version of the common address dialog box. This flag is mutually exclusive with DIALOG_SDI.

DIALOG_SDI
  
> Displays the modeless version of the common address dialog box. This flag is mutually exclusive with DIALOG_MODAL.

MAPI_UNICODE
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.

 _lpulObjType_
  
> [out] A pointer to the type of the opened entry.

 _lppUnk_
  
> [out] A pointer to a pointer of the opened entry.
