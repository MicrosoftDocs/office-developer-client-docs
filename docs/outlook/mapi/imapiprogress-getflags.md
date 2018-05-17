---
title: "IMAPIProgressGetFlags"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProgress.GetFlags
api_type:
- COM
ms.assetid: 7af74fcc-c0df-4f58-a2d4-0a79c96b2e81
description: "Last modified: March 09, 2015"
---

# IMAPIProgress::GetFlags

  
  
**Applies to**: Outlook 
  
Returns flag settings from the progress object for the level of operation on which progress information is calculated.
  
```
HRESULT GetFlags(
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [out] A bitmask of flags that controls the level of operation on which progress information is calculated. The following flag can be returned:
    
MAPI_TOP_LEVEL 
  
> Progress is being calculated for the top-level object, the object that is called by the client to begin the operation. For example, the top-level object in a folder copy operation is the folder that is being copied. When MAPI_TOP_LEVEL is not set, progress is calculated for a lower level object, or subobject. In the folder copy operation, a lower level object is one of the subfolders in the folder that is being copied.
    
## Return value

S_OK 
  
> The flags value was returned successfully.
    
## Remarks

MAPI enables service providers to differentiate between top-level objects and subobjects with the MAPI_TOP_LEVEL flag so that all objects involved in an operation can use the same [IMAPIProgress](imapiprogressiunknown.md) implementation to show progress. This causes the indicator display to proceed smoothly in a single positive direction. Whether the MAPI_TOP_LEVEL flag is set determines how service providers set the other parameters in subsequent calls to the progress object. 
  
The value returned by **GetFlags** is set initially by the implementer and subsequently by the service provider through a call to the [IMAPIProgress::SetLimits](imapiprogress-setlimits.md) method. 
  
## Notes to Implementers

Always initialize the flag to MAPI_TOP_LEVEL and then rely on service providers to clear it when appropriate. Service providers can clear and reset the flag by calling the **IMAPIProgress::SetLimits** method. For more information about how to implement **GetFlags** and the other **IMAPIProgress** methods, see [Implementing a Progress Indicator](implementing-a-progress-indicator.md).
  
## Notes to Callers

When you display a progress indicator, make your first call a call to **IMAPIProgress::GetFlags**. The returned value should be MAPI_TOP_LEVEL, because all implementations initialize the contents of the  _lpulFlags_ parameter to this value. For more information about the sequence of calls to a progress object, see [Display a Progress Indicator](how-to-display-a-progress-indicator.md).
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProgress.cpp  <br/> |CMAPIProgress::GetFlags  <br/> |MFCMAPI uses the **IMAPIProgress::GetFlags** method to determine which flags are set. Returns MAPI_TOP_LEVEL unless flags have been set by using the **IMAPIProgress::SetLimits** method.  <br/> |
   
## See also

#### Reference

[IMAPIProgress::SetLimits](imapiprogress-setlimits.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Display a Progress Indicator](how-to-display-a-progress-indicator.md)
  
[Implementing a Progress Indicator](implementing-a-progress-indicator.md)

