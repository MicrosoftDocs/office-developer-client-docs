---
title: "IMAPIProgressGetMin"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProgress.GetMin
api_type:
- COM
ms.assetid: caceddf1-0f7c-47b5-97bf-17ffe3440a6c
description: "Last modified: March 09, 2015"
---

# IMAPIProgress::GetMin

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the minimum value in the [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) method for which progress information is displayed. 
  
```cpp
HRESULT GetMin(
  ULONG FAR * lpulMin
);
```

## Parameters

 _lpulMin_
  
> [out] A pointer to the minimum number of items in the operation.
    
## Return value

S_OK 
  
> The minimum number of items in the operation has been retrieved.
    
## Remarks

The minimum value represents the start of the operation in numeric form. The value can be a global maximum value, used to represent the scope of the entire progress display, or a local value, used to represent only a part of the display. 
  
The value of the flag setting affects whether the progress object understands the minimum value to be local or global. When the MAPI_TOP_LEVEL flag is set, the minimum value is considered to be global and is used to calculate progress for the entire operation. When MAPI_TOP_LEVEL is not set, the minimum value is considered local, and providers use it internally to display progress for lower level subobjects. Progress objects save the local minimum value only to return it to a provider through a **GetMin** call. 
  
## Notes to implementers

Initialize the minimum value to 1. Service providers can reset this value by calling the **IMAPIProgress::SetLimits** method. For more information about how to implement **GetMin** and the other [IMAPIProgress](imapiprogressiunknown.md) methods, see [Implementing a Progress Indicator](implementing-a-progress-indicator.md).
  
For more information about how and when to make calls to a progress object, see [Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProgress.cpp  <br/> |CMAPIProgress::GetMin  <br/> |MFCMAPI uses the **IMAPIProgress::GetMin** method to get the minimum value for the progress indicator. Returns 1 unless limits have been previously set by calling the **IMAPIProgress::SetLimits** method.  <br/> |
   
## See also



[IMAPIProgress::GetMax](imapiprogress-getmax.md)
  
[IMAPIProgress::Progress](imapiprogress-progress.md)
  
[IMAPIProgress::SetLimits](imapiprogress-setlimits.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Display a Progress Indicator](how-to-display-a-progress-indicator.md)
  
[Implementing a Progress Indicator](implementing-a-progress-indicator.md)

