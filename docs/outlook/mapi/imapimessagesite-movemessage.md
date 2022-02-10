---
title: "IMAPIMessageSiteMoveMessage"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite.MoveMessage
api_type:
- COM
ms.assetid: cd4d7b11-fad0-4f05-a99e-9567abcab45c
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite::MoveMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Moves the current message to a folder.
  
```cpp
HRESULT MoveMessage(
  LPFOLDER pFolderDestination,
  LPMAPIVIEWCONTEXT pViewContext,
  LPCRECT prcPosRect
);
```

## Parameters

 _pFolderDestination_
  
> [in] A pointer to the folder where the message is to be moved.
    
 _pViewContext_
  
> [in] A pointer to a view context object.
    
 _prcPosRect_
  
> [in] A pointer to a [RECT](https://msdn.microsoft.com/library/dd162897%28VS.85%29.aspx) structure that contains the current form's window size and position. The next form displayed also uses this window rectangle. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_NO_SUPPORT 
  
> The operation is not supported by this message site.
    
## Remarks

Form objects call the **IMAPIMessageSite::MoveMessage** method to move the current message to a new folder. 
  
## Notes to implementers

A form viewer's implementation of **MoveMessage** must call the [IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md) method, passing the VCDIR_MOVE flag, before actually moving the message to a new folder. To obtain the **RECT** structure used by a form's window, call the Windows [GetWindowRect](https://msdn.microsoft.com/library/ms633519) function. 
  
For a list of interfaces related to form servers, see [MAPI Form Interfaces](mapi-form-interfaces.md).
  
## Notes to callers

Following the return of **MoveMessage**, forms must check for a current message and then dismiss themselves if none exists. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::MoveMessage  <br/> |Not implemented. |
   
## See also



[IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Form Interfaces](mapi-form-interfaces.md)

