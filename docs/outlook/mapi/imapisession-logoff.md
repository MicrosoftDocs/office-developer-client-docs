---
title: "IMAPISessionLogoff"
description: "Describes the syntax, parameters, return value, and remarks for IMAPISessionLogoff, which ends a MAPI session."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.Logoff
api_type:
- COM
ms.assetid: 93e38f6c-4b67-4f2d-bc94-631efec86852
---

# IMAPISession::Logoff

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Ends a MAPI session.
  
```cpp
HRESULT Logoff(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  ULONG ulReserved
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows to be displayed. This parameter is ignored if the MAPI_LOGOFF_UI flag is not set.
    
 _ulFlags_
  
> [in] A bitmask of flags that control the logoff operation. The following flags can be set:
    
MAPI_LOGOFF_SHARED 
  
> If this session is shared, all clients that logged on by using the shared session should be notified of the logoff in progress. The clients should log off. Any client that is using the shared session can set this flag. MAPI_LOGOFF_SHARED is ignored if the current session is not shared.
    
MAPI_LOGOFF_UI 
  
> **Logoff** can display a dialog box during the operation, possibly prompting the user for confirmation. 
    
 _ulReserved_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The logoff operation was successful.
    
## Remarks

The **IMAPISession::Logoff** method ends a MAPI session. When **Logoff** returns, none of the methods except for [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) can be called. 
  
## Notes to callers

When **Logoff** returns, release the session object by calling its **IUnknown::Release** method. 
  
For more information about ending a session, see [Ending a MAPI Session](ending-a-mapi-session.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIObjects.cpp  <br/> |CMapiObjects::Logoff  <br/> |MFCMAPI uses the **IMAPISession::Logoff** method to log off from the session before releasing it. |
   
> [!NOTE]
> Due to the fast shutdown behavior introduced in Microsoft Office Outlook 2007 Service Pack 2, Microsoft Outlook 2010, and Microsoft Outlook 2013, clients should never pass the **MAPI_LOGOFF_SHARED** parameter to [IMAPISession::Logoff](imapisession-logoff.md). Passing **MAPI_LOGOFF_SHARED** will cause all MAPI clients to begin shutdown and unexpected behavior will occur. 
  
## See also



[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Ending a MAPI Session](ending-a-mapi-session.md)

