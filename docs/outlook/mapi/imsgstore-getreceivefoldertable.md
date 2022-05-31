---
title: "IMsgStoreGetReceiveFolderTable"
description: "IMsgStore GetReceiveFolderTable provides access to the receive folder table, which includes information about all of the receive folders for the message store."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.GetReceiveFolderTable
api_type:
- COM
ms.assetid: d115ab58-07d2-4b49-8e08-2881c2924102
---

# IMsgStore::GetReceiveFolderTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the receive folder table, a table that includes information about all of the receive folders for the message store.
  
```cpp
HRESULT GetReceiveFolderTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable );
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls table access. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **GetReceiveFolderTable** to return successfully, possibly before the table is fully available to the caller. If the table is not fully available, making a subsequent table call can raise an error. 
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lppTable_
  
> [out] A pointer to a pointer to the receive folder table.
    
## Return value

S_OK 
  
> The receive folder table was successfully returned.
    
## Remarks

The **IMsgStore::GetReceiveFolderTable** method provides access to a table that shows the property settings for all of the message store's receive folders. 
  
## Notes to implementers

For a list of required columns in a receive folder table, see [Receive Folder Tables](receive-folder-tables.md). 
  
Implement your receive folder tables to support setting property restrictions on the **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)) property. This enables easy access to particular receive folders.
  
## Notes to callers

Setting the MAPI_UNICODE flag in the _ulFlags_ parameter affects the format of the columns returned from the [IMAPITable::QueryColumns](imapitable-querycolumns.md) and [IMAPITable::QueryRows](imapitable-queryrows.md) methods. This flag also controls the property types in the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnDisplayReceiveFolderTable  <br/> |MFCMAPI uses the **IMsgStore::GetReceiveFolderTable** method to get the receive folder table to display. |
   
## See also



[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

