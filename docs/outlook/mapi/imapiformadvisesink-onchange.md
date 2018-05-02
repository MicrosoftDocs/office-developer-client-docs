---
title: "IMAPIFormAdviseSinkOnChange"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormAdviseSink.OnChange
api_type:
- COM
ms.assetid: d700b40f-e5b2-4d37-bf1f-8fd3dfa0dda5
description: "Last modified: July 23, 2011"
---

# IMAPIFormAdviseSink::OnChange

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Indicates that a change has occurred in the status of the form viewer. 
  
```
HRESULT OnChange(
  ULONG ulDir
);
```

## Parameters

 _ulDir_
  
> [in] A bitmask of flags that provides information about the change that has occurred in the viewer and the expected response in the form. The following flags can be set:
    
VCSTATUS_CATEGORY 
  
> There is a next or previous message in another category. 
    
VCSTATUS_INTERACTIVE 
  
> The form should display a user interface. If this flag is not set, the form should suppress displaying a user interface, even in response to a verb that usually causes a user interface to be displayed. 
    
VCSTATUS_MODAL 
  
> The form is to be modal to the form viewer. 
    
VCSTATUS_NEXT 
  
> There is a next message in the form viewer. 
    
VCSTATUS_PREV 
  
> There is a previous message in the form viewer. 
    
VCSTATUS_READONLY 
  
> Delete, submit, and move operations should be disabled. 
    
VCSTATUS_UNREAD 
  
> There is a next or previous unread message in the form viewer.
    
## Return value

S_OK 
  
> The notification was successful.
    
## Remarks

Form viewers call the **IMAPIFormAdviseSink::OnChange** method to notify the form about a change in a viewer's status. Usually, the only change is setting or clearing the VCSTATUS_NEXT or VCSTATUS_PREVIOUS flag based on the presence or absence of a next or previous message in the viewer. Accordingly, the form object then enables or disables any next or previous actions it supports. 
  
The settings of VCSTATUS_MODAL and VCSTATUS_INTERACTIVE cannot change in a view context after it has been created.
  
## Notes to Implementers

The specific implementation of this method is completely dependent on the specifics of the form. Most form objects use this method to change their user interface (for example, to enable or disable menu commands or buttons to match the viewer status flags parameter).
  
## See also

#### Reference

[IMAPIViewContext::ActivateNext](imapiviewcontext-activatenext.md)
  
[IMAPIFormAdviseSink : IUnknown](imapiformadvisesinkiunknown.md)

