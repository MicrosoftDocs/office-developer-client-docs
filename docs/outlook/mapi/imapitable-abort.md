---
title: "IMAPITableAbort"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.Abort
api_type:
- COM
ms.assetid: 73291a5b-b626-494c-b5d9-f7709e34bac2
---

# IMAPITable::Abort

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Stops any asynchronous operations currently in progress for the table.
  
```cpp
HRESULT Abort( void );
```

## Parameters

None
  
## Return value

S_OK 
  
> One or more asynchronous operations have been stopped.
    
MAPI_E_UNABLE_TO_ABORT 
  
> An asynchronous operation is in progress and cannot be stopped or it has already completed.
    
## Remarks

The **IMAPITable::Abort** method stops any asynchronous operation that is currently in progress. 
  
## Notes to callers

To find out if an asynchronous operation is in progress, call the [IMAPITable::GetStatus](imapitable-getstatus.md) method. 
  
If **Abort** halts the processing of a call to the [IMAPITable::Restrict](imapitable-restrict.md) method, the state of the table will be as it was at the time the **Abort** call is processed. 
  
If **Abort** halts the processing of a call to the [IMAPITable::SortTable](imapitable-sorttable.md) method, the table's sort order is unaffected and remains as it was before the **SortTable** call. 
  
## See also



[IMAPITable::GetStatus](imapitable-getstatus.md)
  
[IMAPITable::Restrict](imapitable-restrict.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

