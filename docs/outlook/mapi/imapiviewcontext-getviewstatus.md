---
title: "IMAPIViewContextGetViewStatus"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewContext.GetViewStatus
api_type:
- COM
ms.assetid: 2e5ec914-7171-41ce-a6fe-78dd80ac32ff
description: "Last modified: March 09, 2015"
---

# IMAPIViewContext::GetViewStatus

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the current viewer status. 
  
```cpp
HRESULT GetViewStatus(
ULONG FAR * lpulStatus
);
```

## Parameters

 _lpulStatus_
  
> [out] Pointer to a bitmask of flags providing the status of the viewer. The following flags can be set:
    
VCSTATUS_CATEGORY 
  
> There is a next or previous message in another category. 
    
VCSTATUS_DELETE 
  
> The form allows messages to be removed. 
    
VCSTATUS_INTERACTIVE 
  
> The form should display a user interface. If this flag is not set, the form should suppress displaying a user interface even in response to a verb that usually causes a user interface to be displayed. 
    
VCSTATUS_MODAL 
  
> The form is modal to the viewer. 
    
VCSTATUS_NEXT 
  
> There is a next message in the view. 
    
VCSTATUS_PREV 
  
> There is a previous message in the view. 
    
VCSTATUS_READONLY 
  
> The message is to be opened in read-only mode. Delete, submit, and move operations should be disabled. 
    
VCSTATUS_UNREAD 
  
> There is a next or previous unread message in the view.
    
## Return value

S_OK 
  
> The viewer's status was successfully returned.
    
## Remarks

Form objects call the **IMAPIViewContext::GetViewStatus** method to determine whether there are more messages to be activated in a form view in either or both directions that is, in the direction in which a **Next** command activates messages, in the direction in which a **Previous** command activates messages, or in both directions. The value pointed to by the  _lpulStatus_ parameter is used to determine whether the VCSTATUS_NEXT and VCSTATUS_PREV flags are valid for [IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md). If the VCSTATUS_DELETE flag is set, but not the VCSTATUS_READONLY flag, then the message can be deleted using the [IMAPIMessageSite::DeleteMessage](imapimessagesite-deletemessage.md) method. 
  
Typically, forms disable menu commands and buttons if they are not valid for the viewer's context. A viewer can alert a form to a change in status by calling its [IMAPIFormAdviseSink::OnChange](imapiformadvisesink-onchange.md) method. 
  
The VCSTATUS_MODAL flag is set if the form must be modal to the window whose handle is passed in the earlier [IMAPIForm::DoVerb](imapiform-doverb.md) call. If VCSTATUS_MODAL is set, the form can use the thread on which the **DoVerb** call was made until the form closes. If VCSTATUS_MODAL is not set, the form should not be modal to this window and must not use the thread. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MyMAPIFormViewer.cpp  <br/> |CMyMAPIFormViewer::GetViewStatus  <br/> |MFCMAPI implements the **IMAPIViewContext::GetViewStatus** method in this function.  <br/> |
   
## See also



[IMAPIMessageSite::GetSiteStatus](imapimessagesite-getsitestatus.md)
  
[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

