---
title: "IMAPIMessageSiteGetFolder"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite.GetFolder
api_type:
- COM
ms.assetid: 9f4b4147-ed98-47cb-a799-ddf028f8e826
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite::GetFolder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the folder in which the current message was created or opened, if such a folder exists. This method returns NULL in the _ppFolder_ parameter for embedded messages, which are not stored directly in a folder. 
  
```cpp
HRESULT GetFolder(
  LPMAPIFOLDER FAR * ppFolder
);
```

## Parameters

 _ppFolder_
  
> [out] A pointer to a pointer to the returned folder.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
S_FALSE 
  
> No folder exists for the message.
    
## Remarks

For a list of interfaces that are related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::GetFolder  <br/> |MFCMAPI uses the **IMAPIMessageSite::GetFolder** method to return the currently cached pointer to the specified folder. |
   
## See also



[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Form Interfaces](mapi-form-interfaces.md)

