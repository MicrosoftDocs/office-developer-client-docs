---
title: "IMAPISupportDoProgressDialog"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.DoProgressDialog
api_type:
- COM
ms.assetid: 74c52b96-e903-444b-8bda-73a08f278c22
description: "Last modified: July 23, 2011"
---

# IMAPISupport::DoProgressDialog

  
  
**Applies to**: Outlook 
  
Retrieves a progress object that displays a progress indicator.
  
```
HRESULT DoProgressDialog(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPMAPIPROGRESS FAR * lppProgress
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the progress indicator.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the progress object should calculate progress. The following flag can be set:
    
MAPI_TOP_LEVEL 
  
> Progress is calculated for a top-level item, such as a parent folder. The progress object should use the values in the [IMAPIProgress::Progress](imapiprogress-progress.md) method's  _ulCount_ and  _ulTotal_ parameters — which indicate the current item and the total items in the operation, respectively — to increment the progress indicator for the operation. 
    
 _lppProgress_
  
> [out] A pointer to a pointer to the progress object.
    
## Return value

S_OK 
  
> The progress object was successfully retrieved.
    
## Remarks

The **IMAPISupport::DoProgressDialog** method is implemented for address book and message store provider support objects. These providers call **DoProgressDialog** to access the MAPI implementation of the [IMAPIProgress](imapiprogressiunknown.md) interface, which calculates the progress information and displays a standard dialog box. 
  
For information about how to use a progress object and the **IMAPIProgress** interface, see [Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## See also

#### Reference

[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
  
[IMAPIProgress::Progress](imapiprogress-progress.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)
#### Concepts

[Display a Progress Indicator](how-to-display-a-progress-indicator.md)

