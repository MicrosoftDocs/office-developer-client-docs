---
title: "IMAPITableFindRow"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.FindRow
api_type:
- COM
ms.assetid: 6511368c-9777-497e-9eea-cf390c04b92e
description: "Last modified: March 09, 2015"
---

# IMAPITable::FindRow

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Finds the next row in a table that matches specific search criteria and moves the cursor to that row.
  
```cpp
HRESULT FindRow(
LPSRestriction lpRestriction,
BOOKMARK BkOrigin,
ULONG ulFlags
);
```

## Parameters

 _lpRestriction_
  
> [in] A pointer to an [SRestriction](srestriction.md) structure that describes the search criteria. 
    
 _BkOrigin_
  
> [in] A bookmark identifying the row where **FindRow** should begin its search. A bookmark can be created using the [IMAPITable::CreateBookmark](imapitable-createbookmark.md) method, or one of the following predefined values can be passed. 
    
BOOKMARK_BEGINNING 
  
> Searches from the beginning of the table. 
    
BOOKMARK_CURRENT 
  
> Searches from the row in the table where the cursor is located. 
    
BOOKMARK_END 
  
> Searches from the end of the table. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the direction of the search. The following flag can be set:
    
DIR_BACKWARD 
  
> Searches backward from the row identified by the bookmark.
    
## Return value

S_OK 
  
> The find operation was successful.
    
MAPI_E_INVALID_BOOKMARK 
  
> The bookmark in the  _BkOrigin_ parameter is invalid because it has been removed or because it is beyond the last row requested. 
    
MAPI_E_NOT_FOUND 
  
> No rows were found that matched the restriction.
    
MAPI_W_POSITION_CHANGED
  
> The call succeeded, but the bookmark used in the operation is no longer set at the same row as when it was last used; if the bookmark has not been used, it is no longer in the same position as when it was created. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. See [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPITable::FindRow** method locates the first row in the table to match a set of search criteria described in the **SRestriction** structure pointed to by the  _lpRestriction_ parameter. 
  
Usually, **FindRow** searches forward from the specified bookmark. The caller can set the search to move backward from the bookmark by setting the DIR_BACKWARD flag in the  _ulFlags_ parameter. Searching forward starts from the current bookmark; searching backward starts from the row prior to the bookmark. The end position of the search is just before the first row found that satisfied the restriction. 
  
If the row pointed to by the bookmark in the  _BkOrigin_ parameter no longer exists in the table and the table cannot establish a new position for the bookmark, **FindRow** returns MAPI_E_INVALID_BOOKMARK. If the row pointed to by  _BkOrigin_ no longer exists and the table is able to establish a new position for the bookmark, **FindRow** returns MAPI_W_POSITION_CHANGED. 
  
If the bookmark passed in  _BkOrigin_ is either BOOKMARK_BEGINNING or BOOKMARK_END, **FindRow** returns MAPI_E_NOT_FOUND if no matching row is found. If the bookmark used in  _BkOrigin_ is BOOKMARK_CURRENT, **FindRow** can return MAPI_W_POSITION_CHANGED but not MAPI_E_INVALID_BOOKMARK because there is always a current cursor position. 
  
The **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property column is required for all tables, and all implementations of **FindRow** are required to support calls seeking a row based on PR_INSTANCE_KEY. 
  
## Notes to implementers

The type of prefix searching performed by **FindRow** is only useful when the search follows the same direction as the table organization. In order to achieve the required behavior, the comparison function implied by the **RELOP_GE** passed in the property restriction structure should be the same comparison function on which the table sort order is based. 
  
## Notes to callers

You can use **FindRow** to support scrolling based on strings typed in by the user, especially in list boxes within address dialog boxes. In this type of scrolling, users enter progressively longer prefixes of a desired string value, and you can periodically issue a **FindRow** call to jump to the first row that matches the prefix. Which direction the cursor jumps depends on which direction the search is set to run. 
  
To use **FindRow**, a bookmark must be set. The string search can originate from any bookmark, including from the preset bookmarks indicating the current position and the beginning and end of the table. If there are a large number of rows in the table, the search operation can be slow.
  
Use a restriction to find a string prefix for scrolling as follows. For forward searching on a column sorted in ascending order and for backward searching on a column sorted in descending order, pass a property restriction structure in the  _lpRestriction_ parameter with the relation **RELOP_GE** and the appropriate property tag and prefix, using the format  _tag_ **GE** _prefix_. 
  
For more information about using restriction structures to specify a filter, see [About Restrictions](about-restrictions.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|ContentsTableListCtrl.cpp  <br/> |DwThreadFuncLoadTable  <br/> |MFCMAPI uses the **IMAPITable::FindRow** method to find rows which match a restriction.  <br/> |
   
## See also



[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[SPropertyRestriction](spropertyrestriction.md)
  
[SRestriction](srestriction.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

