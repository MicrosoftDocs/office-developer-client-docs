---
title: "IMAPITableRestrict"
description: "IMAPITableRestrict applies a filter to a table, reducing the row set to only those rows matching the specified criteria."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.Restrict
api_type:
- COM
ms.assetid: a5bfc190-b58f-44c3-893c-8727df14ee58
---

# IMAPITable::Restrict

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Applies a filter to a table, reducing the row set to only those rows matching the specified criteria.
  
```cpp
HRESULT Restrict(
LPSRestriction lpRestriction,
ULONG ulFlags
);
```

## Parameters

 _lpRestriction_
  
> [in] Pointer to an [SRestriction](srestriction.md) structure defining the conditions of the filter. Passing NULL in the _lpRestriction_ parameter removes the current filter. 
    
 _ulFlags_
  
> [in] Bitmask of flags that controls the timing of the restriction operation. The following flags can be set:
    
TBL_ASYNC 
  
> Starts the operation asynchronously and returns before the operation completes.
    
TBL_BATCH 
  
> Defers evaluation of the filter until the data in the table is required.
    
## Return value

S_OK 
  
> The filter was successfully applied.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the restriction operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
MAPI_E_TOO_COMPLEX 
  
> The table cannot perform the operation because the particular filter pointed to by the  _lpRestriction_ parameter is too complicated. 
    
## Remarks

The **IMAPITable::Restrict** method establishes a restriction, or filter, on a table. If there is a previous restriction, it is discarded and the new one applied. Applying a restriction has no affect on the underlying data of a table; it simply alters the view by limiting the rows that can be retrieved to rows containing data that satisfy the restriction. 
  
There are several different types of restrictions, each described with a different structure. The [SRestriction](srestriction.md) structure contains two members: a value that indicates the type of restriction and the specific structure applicable for that type. 
  
Notifications for table rows that are hidden from view by calls to **Restrict** are never generated. 
  
A property restriction on a multivalued property works like a restriction on a single-valued property. A multivalued property to be used in a property restriction must have the MVI_FLAG flag set. If it doesn't have this flag set, it is treated as a totally ordered tuple. A comparison of two multivalued columns compares the column elements in order, reporting the relation of the columns at the first inequality. Equality is returned only if the columns compared contain the same values in the same order. If one column has fewer values than the other, the reported relation is that of a null value to the other value.
  
For more information about restrictions, see [About Restrictions](about-restrictions.md).
  
> [!NOTE]
> If you create dynamic queries to search for data on the server, use the **FindRow** method instead of using the **Restrict** method and the **QueryRows** method together. The **Restrict** method creates a cached view that is used to evaluate all messages added to or modified in the base folder. If a client application uses the **Restrict** method for each dynamic query, a cached view will be created for each query. 
  
## Notes to callers

To discard the current restriction without creating a new one, pass NULL in  _lpRestriction_.
  
If another asynchronous table call is in progress, causing **Restrict** to return MAPI_E_BUSY, you can call [IMAPITable::Abort](imapitable-abort.md) to stop the call. 
  
 **Restrict** operates synchronously unless you set one of the flags. If you set the TBL_BATCH flag, **Restrict** postpones the evaluation of the restriction unless you request the data. If the TBL_ASYNC flag is set, **Restrict**operates asynchronously, potentially returning before the completion of the operation.
  
All bookmarks for a table are discarded when a call to **Restrict** is made, and BOOKMARK_CURRENT, the current cursor position, is set to the beginning of the table. 
  
If you attempt to impose a property restriction on a property that is not in the table's column set, the results are undefined. Whenever you are unsure as to whether a property is supported in a table, combine the property restriction with an exists restriction. The exists restriction checks for the existence of the property before attempting to impose the property restriction. 
  
Do not expect to receive a table notification on a row that has been filtered from a table due to a restriction.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::ApplyRestriction  <br/> |MFCMAPI uses the **IMAPITable::Restrict** method to set a restriction on a table. |
   
## See also



[IMAPITable::Abort](imapitable-abort.md)
  
[IMAPITable::FindRow](imapitable-findrow.md)
  
[IMAPITable::GetRowCount](imapitable-getrowcount.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[SPropertyRestriction](spropertyrestriction.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

