---
title: "IABContainerDeleteEntries"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABContainer.DeleteEntries
api_type:
- COM
ms.assetid: 70a24811-0c41-4b44-8c63-7ef807bc9051
description: "Last modified: March 09, 2015"
---

# IABContainer::DeleteEntries

  
  
**Applies to**: Outlook 
  
Removes one or more entries, typically messaging users, distribution lists, or other containers.
  
```cpp
HRESULT DeleteEntries(
  LPENTRYLIST lpEntries,
  ULONG ulFlags
);
```

## Parameters

 _lpEntries_
  
> [in] A pointer to an array of [ENTRYLIST](entrylist.md) structures that contain entry identifiers that represent the entries being deleted. 
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The specified entries have been successfully deleted. 
    
MAPI_W_PARTIAL_COMPLETION 
  
> The call succeeded, but one or more of the entries could not be deleted. When this value is returned, the call should be handled as successful. To test for this value, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|Abdlg.cpp  <br/> |CabDlg::OnDeleteSelectedItem  <br/> |MFCMAPI uses the **DeleteEntries** method to delete a specific entry from an address book container.  <br/> |
   
## See also



[IABContainer : IMAPIContainer](iabcontainerimapicontainer.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

