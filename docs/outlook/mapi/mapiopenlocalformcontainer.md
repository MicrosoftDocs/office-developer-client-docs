---
title: "MAPIOpenLocalFormContainer"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MAPIOpenLocalFormContainer
api_type:
- COM
ms.assetid: 1c53170f-03a6-4a05-913e-de8eeadea692
description: "Last modified: March 09, 2015"
---

# MAPIOpenLocalFormContainer

  
  
**Applies to**: Outlook 
  
Returns an interface pointer to the local form library. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
MAPIOpenLocalFormContainer(
  LPMAPIFORMCONTAINER FAR * ppfcnt
);
```

## Parameters

 _ppfcnt_
  
> [out] Pointer to a pointer to the local form library interface.
    
## Return value

None.
  
## Remarks

The interface to which a pointer is returned can be used by third-party installation programs to install application-specific forms into the library without the program first having to log on to MAPI. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnMAPIOpenLocalFormContainer  <br/> |MFCMAPI uses the **MAPIOpenLocalFormContainer** method to open the local form container to render in a new window.  <br/> |
   
## See also

#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

