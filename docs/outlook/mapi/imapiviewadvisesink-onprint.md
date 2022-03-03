---
title: "IMAPIViewAdviseSinkOnPrint"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewAdviseSink.OnPrint
api_type:
- COM
ms.assetid: d16219a0-268c-428d-9f02-4f06eb5b6d7d
---

# IMAPIViewAdviseSink::OnPrint

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Notifies the form viewer of the printing status of a form.
  
```cpp
HRESULT OnPrint(
ULONG dwPageNumber,
HRESULT hrStatus
);
```

## Parameters

 _dwPageNumber_
  
> [in] Number of the last page printed.
    
 _hrStatus_
  
> [in] An HRESULT value indicating the status of the print job. Possible values are:
    
S_FALSE 
  
> The printing job has finished successfully.
    
S_OK 
  
> The printing job is in progress.
    
FAILED 
  
> The printing job was terminated due to a failure.
    
## Return value

S_OK 
  
> The notification succeeded.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the Cancel button in a dialog box. 
    
## Remarks

Form objects call the **IMAPIViewAdviseSink::OnPrint** method while printing to inform the viewer of printing progress. 
  
## Notes to callers

If the printing job involves multiple pages, you can call **OnPrint** after each page is printed. Set  _dwPageNumber_ to the page currently being printed and  _hrStatus_ to S_OK. When the printing job is complete, call **OnPrint** with  _dwPageNumber_ set to the last page printed and  _hrStatus_ set to S_FALSE. 
  
For more information about form notifications, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## See also



[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)

