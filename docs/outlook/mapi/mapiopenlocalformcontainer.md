---
title: "MAPIOpenLocalFormContainer"
description: Describes the MAPIOpenLocalFormContainer function and provides syntax, parameters, return value, remarks, and MFCMAPI reference.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.MAPIOpenLocalFormContainer
api_type:
- COM
ms.assetid: 1c53170f-03a6-4a05-913e-de8eeadea692
---

# MAPIOpenLocalFormContainer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns an interface pointer to the local form library. 
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
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
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnMAPIOpenLocalFormContainer  <br/> |MFCMAPI uses the **MAPIOpenLocalFormContainer** method to open the local form container to render in a new window. |
   
## See also



[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

