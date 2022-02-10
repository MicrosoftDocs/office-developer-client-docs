---
title: "IMAPIProgressGetMax"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProgress.GetMax
api_type:
- COM
ms.assetid: 88a910ed-b55a-4e5b-a43d-eb3ea795a70e
description: "Last modified: March 09, 2015"
---

# IMAPIProgress::GetMax

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the maximum number of items in the operation for which progress information is displayed.
  
```cpp
HRESULT GetMax(
  ULONG FAR * lpulMax
);
```

## Parameters

 _lpulMax_
  
> [out] A pointer to the maximum number of items in the operation.
    
## Return value

S_OK 
  
> The maximum number of items in the operation has been retrieved.
    
## Remarks

The maximum value represents the end of the operation in numeric form. The value can be a global maximum value, used to represent the scope of the entire progress display, or a local value, used to represent only a part of the display. 
  
The value of the flag setting affects whether the progress object understands the maximum value to be local or global. When the MAPI_TOP_LEVEL flag is set, the maximum value is considered to be global and is used to calculate progress for the entire operation. When MAPI_TOP_LEVEL is not set, the maximum value is considered to be local, and providers use it internally to display progress for lower level subobjects. Progress objects save the local maximum value only to return it to a provider through a **GetMax** call. 
  
For more information about how and when to make calls to a progress object, see [Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## Notes to implementers

Initialize the maximum value to 1000. Service providers can reset this value by calling the [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) method. For more information about how to implement **GetMax** and the other [IMAPIProgress](imapiprogressiunknown.md) methods, see [Implementing a Progress Indicator](implementing-a-progress-indicator.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProgress.cpp  <br/> |CMAPIProgress::GetMax  <br/> |MFCMAPI uses the **IMAPIProgress::GetMax** method to get the maximum value for the progress object. Returns 1000 unless limits have previously been set with the **IMAPIProgress::SetLimits** method. |
   
## See also



[IMAPIProgress::GetMin](imapiprogress-getmin.md)
  
[IMAPIProgress::Progress](imapiprogress-progress.md)
  
[IMAPIProgress::SetLimits](imapiprogress-setlimits.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Display a Progress Indicator](how-to-display-a-progress-indicator.md)
  
[Implementing a Progress Indicator](implementing-a-progress-indicator.md)

