---
title: "IMAPITableWaitForCompletion"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.WaitForCompletion
api_type:
- COM
ms.assetid: 7663c640-396e-4720-9345-370d0856bd49
description: "Last modified: July 23, 2011"
---

# IMAPITable::WaitForCompletion

  
  
**Applies to**: Outlook 
  
Suspends processing until one or more asynchronous operations in progress on the table have completed.
  
```
HRESULT WaitForCompletion(
ULONG ulFlags,
ULONG ulTimeout,
ULONG FAR * lpulTableStatus
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
 _ulTimeout_
  
> [in] Maximum number of milliseconds to wait for the asynchronous operation or operations to complete. To wait indefinitely until completion occurs, set  _ulTimeout_ to 0xFFFFFFFF. 
    
 _lpulTableStatus_
  
> [in, out] On input, either a valid pointer or NULL. On output, if  _lpulTableStatus_ is a valid pointer, it points to the most recent status of the table. If  _lpulTableStatus_ is NULL, no status information is returned. If **WaitForCompletion** returns an unsuccessful HRESULT value, the contents of  _lpulTableStatus_ are undefined. 
    
## Return value

S_OK 
  
> The wait operation was successful.
    
MAPI_E_NO_SUPPORT 
  
> The table does not support waiting for the completion of asynchronous operations.
    
MAPI_E_TIMEOUT 
  
> The asynchronous operation or operations did not complete in the specified time.
    
## Remarks

The **IMAPITable::WaitForCompletion** method suspends processing until any asynchronous operations currently under way for the table have completed. **WaitForCompletion** can allow the asynchronous operations either to fully complete or to run for a certain number of milliseconds, as indicated by  _ulTimeout_, before being interrupted. To detect asynchronous operations in progress, call the [IMAPITable::GetStatus](imapitable-getstatus.md) method. 
  
## See also

#### Reference

[IMAPITable::GetRowCount](imapitable-getrowcount.md)
  
[IMAPITable::GetStatus](imapitable-getstatus.md)
  
[IMAPITable::Restrict](imapitable-restrict.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

