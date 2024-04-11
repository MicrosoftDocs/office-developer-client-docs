---
title: "IMAPIProgressProgress"
description: "IMAPIProgressProgress updates the progress indicator with a display of the progress as it is made toward completion of the operation."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProgress.Progress
api_type:
- COM
ms.assetid: edbf7623-a64e-43b8-8379-e3cde2433d91
---

# IMAPIProgress::Progress

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Updates the progress indicator with a display of the progress as it is made toward completion of the operation. 
  
```cpp
HRESULT Progress(
  ULONG ulValue,
  ULONG ulCount,
  ULONG ulTotal
);
```

## Parameters

 _ulValue_
  
> [in] A number that indicates the current level of progress (calculated from the  _ulCount_ and  _ulTotal_ parameters or from the  _lpulMin_ and  _lpulMax_ parameters of the [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) method) between the global lower limit and the global upper limit. 
    
 _ulCount_
  
> [in] A number that indicates the currently processed item relative to the total.
    
 _ulTotal_
  
> [in] The total number of items to be processed during the operation.
    
## Return value

S_OK 
  
> The progress indicator was successfully updated.
    
## Notes to implementers

The  _ulValue_ parameter will be equal to the global minimum value only at the start of the operation and to the global maximum value only at the completion of the operation. 
  
Use the  _ulCount_ and  _ulTotal_ parameters, if available, to display an optional message such as "5 items completed out of 10." If  _ulCount_ and  _ulTotal_ are set to 0, decide whether to visually change the progress indicator. Some service providers set these parameters to 0 to indicate that they are processing a subobject whose progress is monitored relative to a parent object. In this situation, it makes sense to change the display only when the parent object reports progress. Some service providers pass 0 for these parameters every time. 
  
For more information about how to implement **Progress** and the other [IMAPIProgress](imapiprogressiunknown.md) methods, see [Implementing a Progress Indicator](implementing-a-progress-indicator.md).
  
## Notes to callers

Not all three of the parameters to **IMAPIProgress::Progress** are required. The only parameter that is required is  _ulValue_, a number that indicates the percentage of progress. If the MAPI_TOP_LEVEL flag is set, you can also pass an object count and an object total. Some implementations use these values to display a phrase such as "5 items completed out of 10" with the progress indicator. 
  
If you are copying all messages in a single folder, set  _ulTotal_ to the total number of messages being copied. If you are copying a folder, set  _ulTotal_ to the number of subfolders in the folder. If the folder to be copied contains no subfolders and only messages, set  _ulTotal_ to 1. 
  
For more information about how and when to make calls to a progress object, see [Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProgress.cpp  <br/> |CMAPIProgress::Progress  <br/> |MFCMAPI uses the **IMAPIProgress::Progress** method to update the MFCMAPI status bar with the current percentage of progress, calculated from  _uValue_ and the current maximum and minimum values. |
   
## See also



[IMAPIProgress::SetLimits](imapiprogress-setlimits.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Display a Progress Indicator](how-to-display-a-progress-indicator.md)
  
[Implementing a Progress Indicator](implementing-a-progress-indicator.md)

