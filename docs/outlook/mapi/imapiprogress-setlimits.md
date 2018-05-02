---
title: "IMAPIProgressSetLimits"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProgress.SetLimits
api_type:
- COM
ms.assetid: 63c9e316-ee53-4065-8154-449639643ff7
description: "Last modified: March 09, 2015"
---

# IMAPIProgress::SetLimits

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Sets the lower and upper limits for the number of items in the operation, and the flags that control how progress information is calculated for the operation.
  
```
HRESULT SetLimits(
  LPULONG lpulMin,
  LPULONG lpulMax,
  LPULONG lpulFlags
);
```

## Parameters

 _lpulMin_
  
> [in] A pointer to a variable that contains the lower limit of items in the operation.
    
 _lpulMax_
  
> [in] A pointer to a variable that contains the upper limit of items in the operation.
    
 _lpulFlags_
  
> [in] A bitmask of flags that controls the level of operation on which progress information is calculated. The following flag can be set:
    
MAPI_TOP_LEVEL 
  
> Uses the values in the [IMAPIProgress::Progress](imapiprogress-progress.md) method's  _ulCount_ and  _ulTotal_ parameters, which indicate the currently processed item and the total items, respectively, to increment progress on the operation. When this flag is set, the values of the global lower and upper limits have to be set. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Service providers call the **IMAPIProgress::SetLimits** method to set or clear the MAPI_TOP_LEVEL flag and to set local and global minimum and maximum values. The value of the flag setting affects whether the progress object understands the minimum and maximum values to be local or global. When the MAPI_TOP_LEVEL flag is set, these values are considered global and are used to calculate progress for the entire operation. Progress objects initialize the global minimum value to 1 and the global maximum value to 1000. 
  
When MAPI_TOP_LEVEL is not set, the minimum and maximum values are considered local, and providers use them internally to display progress for lower level subobjects. Progress objects save the local minimum and maximum values only so that they can be returned to providers when the [IMAPIProgress::GetMin](imapiprogress-getmin.md) and [IMAPIProgress::GetMax](imapiprogress-getmax.md) methods are called. 
  
For more information about how to implement **SetLimits** and the other [IMAPIProgress](imapiprogressiunknown.md) methods, see [Implementing a Progress Indicator](implementing-a-progress-indicator.md).
  
For more information about how and when to make calls to a progress object, see [How to: Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProgress.cpp  <br/> |CMAPIProgress::SetLimits  <br/> |MFCMAPI uses the **IMAPIProgress::SetLimits** method to set the maximum and minimum limits and flags for the progress object.  <br/> |
   
## See also

#### Reference

[IMAPIProgress::GetMax](imapiprogress-getmax.md)
  
[IMAPIProgress::GetMin](imapiprogress-getmin.md)
  
[IMAPIProgress::Progress](imapiprogress-progress.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[How to: Display a Progress Indicator](how-to-display-a-progress-indicator.md)
  
[Implementing a Progress Indicator](implementing-a-progress-indicator.md)

