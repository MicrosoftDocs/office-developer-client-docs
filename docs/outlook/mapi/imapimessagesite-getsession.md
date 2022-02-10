---
title: "IMAPIMessageSiteGetSession"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite.GetSession
api_type:
- COM
ms.assetid: c35d9e38-f4cf-4908-aaa1-a4263b58f7e8
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite::GetSession

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the MAPI session in which the current message was created or opened.
  
```cpp
HRESULT GetSession(
  LPMAPISESSION FAR * ppSession
);
```

## Parameters

 _ppSession_
  
> [out] A pointer to a pointer to the returned session object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
S_FALSE 
  
> No session exists for the current message.
    
## Remarks

For a list of interfaces that are related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::GetSession  <br/> |MFCMAPI uses the **IMAPIMessageSite::GetSession** method to return the currently cached session pointer, if it is available. |
   
## See also



[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

