---
title: "IMAPITableSetColumns"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.SetColumns
api_type:
- COM
ms.assetid: 9a39cf8d-df0f-493c-b272-f15c65b3f15e
description: "Last modified: March 09, 2015"
---

# IMAPITable::SetColumns

  
  
**Applies to**: Outlook 
  
Defines the particular properties and order of properties to appear as columns in the table.
  
```
HRESULT SetColumns(
LPSPropTagArray lpPropTagArray,
ULONG ulFlags
);
```

## Parameters

 _lpPropTagArray_
  
> [in] Pointer to an array of property tags identifying properties to be included as columns in the table. The property type portion of each tag can be set to a valid type or to **PR_NULL** to reserve space for subsequent additions. The  _lpPropTagArray_ parameter cannot be set to NULL; every table must have at least one column. 
    
 _ulFlags_
  
> [in] Bitmask of flags that controls the return of an asynchronous call to **SetColumns**, for example when **SetColumns** is used in notification. The following flags can be set: 
    
TBL_ASYNC 
  
> Requests that the column setting operation be performed asynchronously causing **SetColumns** to potentially return before the operation has fully completed. 
    
TBL_BATCH 
  
> Permits the table to postpone the column setting operation until the data is actually required.
    
## Return value

S_OK 
  
> The column setting operation was successful.
    
MAPI_E_BUSY 
  
> Another operation is in progress that prevents the column setting operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.
    
## Remarks

The column set of a table is the group of properties that make up the columns for the rows in the table. There is a default column set for each type of table. The default column set is made up of the properties that the table implementer automatically includes. Table users can alter this default set by calling the **IMAPITable::SetColumns** method. They can request that other columns be added to the default set if the table implementer supports them that columns be removed, or that the order of columns be changed. **SetColumns** specifies the columns that are returned with each row and the order of these columns within the row. 
  
The success of the **SetColumns** operation is apparent only after a subsequent call has been made to retrieve the data of the table. It is then that any errors are reported. 
  
## Notes to Implementers

Some providers allow a **SetColumns** call to order only table columns that are part of the available columns for a table view. Other providers allow a **SetColumns** call to order all table columns, including those containing properties not in the original column set. 
  
When TBL_BATCH is set for asynchronous operations, providers should return a property type of PT_ERROR and a property value of NULL for columns that are not supported.
  
You do not need to respond to the TBL_ASYNC flag requesting that the operation be asynchronous. If you do not support asynchronous column set definition, perform the operation synchronously. If you can support the TBL_ASYNC flag and another asynchronous operation is still in progress, return MAPI_E_BUSY. Otherwise, return S_OK regardless of whether or not you support all of the properties included in the property tag array. Errors resulting from unsupported properties should be returned from **IMAPITable** methods that retrieve data, such as **QueryRows**. 
  
Do not generate notifications for table rows that are hidden from view by calls to **Restrict**. 
  
When sending table notifications, the order of the properties in the **row** member of the [TABLE_NOTIFICATION](table_notification.md) structure and the order specified by the most recent **SetColumns** call must be the same as of the time that the notification request was sent. 
  
Another flag, TBL_BATCH, allows callers to specify that the table implementer can defer evaluating the results of the operation until a later time. Whenever possible, callers should set this flag because batched operation improves performance.
  
It is often convenient for callers to reserve some columns in the retrieved row set for values to be added later. Callers do this by placing **PR_NULL** ( [PidTagNull](pidtagnull-canonical-property.md)) at the desired positions in the property tag array passed to **SetColumns**; the table will then pass back **PR_NULL** at those positions in all rows retrieved with **QueryRows**.
  
## Notes to Callers

When building the property tag array for the  _lpPropTagArray_ parameter, order the tags in the order that you want the columns to appear in the table view. 
  
You can specify multivalued properties to be included in the column set by applying the multivalued instance flag, or MVI_FLAG constant, to the property tag. Set this flag by passing the property tag for the single-valued version of the property as a parameter to the MVI_PROP macro as follows:
  
```
MVI_PROP(ulPropTag)

```

The MVI_PROP macro will set MVI_FLAG for the property, turning the tag into a multivalued tag. If you erroneously try to call MVI_PROP on a single-valued property, MAPI will ignore the call and leave the property tag unchanged. 
  
You can include property tags set to **PR_NULL** in the property tag array to reserve space in the column set. Reserving space allows you to add to a column set without having to allocate a new property tag array. 
  
When your call to **SetColumns** causes a change to the order of a table's columns and one or more of these columns represent a multivalued property, it is possible for the number of rows in the table to increase. If this occurs, all of the bookmarks for the table are discarded. For more information about how multivalued columns affect tables, see [Working with Multivalued Columns](working-with-multivalued-columns.md).
  
Setting columns is by default a synchronous operation. However, you can allow the table to postpone the operation until such time as the data is needed by setting the TBL_BATCH flag. Setting this flag can improve performance. Another flag, TBL_ASYNC, makes the operation asynchronous, allowing **SetColumns** to return before the operation is complete. To determine when completion occurs, call [IMAPITable::GetStatus](imapitable-getstatus.md).
  
If a call to **SetColumns** returns MAPI_E_BUSY, indicating that another operation is preventing your operation from starting, you can call [IMAPITable::Abort](imapitable-abort.md) to stop the operation in progress. 
  
You can also call [HrAddColumnsEx](hraddcolumnsex.md) to change a column set. The difference between **HrAddColumnsEx** and **IMAPITable::SetColumns** is that **HrAddColumnsEx** is less flexible; it can only add columns. The additional columns are placed at the beginning of the column set; all existing columns appear following these columns. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |CContentsTableListCtrl::DoSetColumns  <br/> |MFCMAPI uses the **IMAPITable::SetColumns** method to set the desired columns for the table.  <br/> |
   
## See also

#### Reference

[HrQueryAllRows](hrqueryallrows.md)
  
[IMAPITable::Abort](imapitable-abort.md)
  
[IMAPITable::GetRowCount](imapitable-getrowcount.md)
  
[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::Restrict](imapitable-restrict.md)
  
[IMAPITable::SortTable](imapitable-sorttable.md)
  
[SPropTagArray](sproptagarray.md)
  
[SPropValue](spropvalue.md)
  
[SRowSet](srowset.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

