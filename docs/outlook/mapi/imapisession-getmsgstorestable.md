---
title: "IMAPISessionGetMsgStoresTable"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.GetMsgStoresTable
api_type:
- COM
ms.assetid: 77db2dff-4534-440f-a05c-635711cbc2c3
description: "Last modified: March 09, 2015"
---

# IMAPISession::GetMsgStoresTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the message store table that contains information about all the message stores in the session profile.
  
```cpp
HRESULT GetMsgStoresTable(
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
  
> [out] A pointer to a pointer to the message store table.
    
## Return value

S_OK 
  
> The table was successfully returned.
    
MAPI_E_BAD_CHARWIDTH 
  
> The MAPI_UNICODE flag was set and the session does not support Unicode.
    
## Remarks

The **IMAPISession::GetMsgStoresTable** method retrieves a pointer to the message store table, a table maintained by MAPI that contains information about each open message store in the profile. 
  
For a complete list of required and optional columns in the message store table, see [Message Store Tables](message-store-tables.md). 
  
## Notes to callers

Because MAPI updates the message store table during the session whenever changes occur, call the **Advise** method of the message store table to register to be notified of these changes. Possible changes include the addition of new message stores, removal of existing stores, and changes to the default store. 
  
Setting the MAPI_UNICODE flag in the  _ulFlags_ parameter affects the format of the columns returned from the [IMAPITable::QueryColumns](imapitable-querycolumns.md) and [IMAPITable::QueryRows](imapitable-queryrows.md) methods. This flag also controls the property types in the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnOpenMessageStoreTable  <br/> |MFCMAPI uses the **IMAPISession::GetMsgStoresTable** method to obtain the message store table so that it can be rendered in the main dialog box of MFCMAPI.  <br/> |
   
## See also



[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
  
[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[Message Store Tables](message-store-tables.md)

