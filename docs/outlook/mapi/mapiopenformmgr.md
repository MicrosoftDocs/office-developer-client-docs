---
title: "MAPIOpenFormMgr"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MAPIOpenFormMgr
api_type:
- COM
ms.assetid: 5b624954-d975-4d5e-84d7-74e096ac30af
description: "Last modified: March 09, 2015"
---

# MAPIOpenFormMgr

  
  
**Applies to**: Outlook 
  
Opens an [IMAPIFormMgr](imapiformmgriunknown.md) interface on a form library provider object in the context of an existing session. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```
MAPIOpenFormMgr(
  LPMAPISESSION pSession,
  LPMAPIFORMMGR FAR * ppmgr
);
```

## Parameters

 _pSession_
  
> [in] Pointer to the session in use by the client application.
    
 _ppmgr_
  
> [out] Pointer to the returned **IMAPIFormMgr** interface. 
    
## Return value

None.
  
## Remarks

After a client application makes a call to the **MAPIOpenFormMgr** function, most subsequent forms-related interactions take place through the form library provider or an interface returned by the form library provider. The **IMAPIFormMgr** interface allows the client to work with message handlers and perform resolutions between message classes and form libraries. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp opens the form manager so a form can be selected.  <br/> |CMainDlg::OnSelectForm  <br/> |MFCMAPI uses the **MAPIOpenFormMgr** method to open the form manager so a form can be selected.  <br/> |
   
## See also

#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

