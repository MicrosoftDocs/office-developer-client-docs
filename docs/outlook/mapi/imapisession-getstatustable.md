---
title: "IMAPISessionGetStatusTable"
description: "IMAPISessionGetStatusTable provides access to the status table, a table that contains information about all the MAPI resources in the session."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.GetStatusTable
api_type:
- COM
ms.assetid: 53428f8d-4838-46d1-a0ab-cafb194f4cc3
---

# IMAPISession::GetStatusTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the status table, a table that contains information about all the MAPI resources in the session.
  
```cpp
HRESULT GetStatusTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that determines the format for columns that are character strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The string columns are in Unicode format. If the MAPI_UNICODE flag is not set, the string columns are in ANSI format.
    
 _lppTable_
  
> [out] A pointer to a pointer to the status table.
    
## Return value

S_OK 
  
> The table was successfully returned.
    
## Remarks

The **IMAPISession::GetStatusTable** method provides access to the status table that contains information about all of the MAPI resources in the session. There is one row in the table for information about the MAPI subsystem, one row for the MAPI spooler, one row for the integrated address book, and one row for each service provider in the profile. 
  
For a complete list of required and optional columns in the status table, see [Status Tables](status-tables.md). 
  
Setting the MAPI_UNICODE flag in the _ulFlags_ parameter affects the format of the columns returned from the [IMAPITable::QueryColumns](imapitable-querycolumns.md) and [IMAPITable::QueryRows](imapitable-queryrows.md) methods. This flag also controls the property types in the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnStatusTable  <br/> |MFCMAPI uses the **IMAPISession::GetStatusTable** method to obtain the status table to be rendered. |
   
## See also



[IMAPITable : IUnknown](imapitableiunknown.md)
  
[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Status Tables](status-tables.md)

