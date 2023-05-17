---
title: "IMAPITableSeekRow"
description: "Describes the syntax, parameters, and return value of IMAPITableSeekRow, which moves the cursor to a specific position in the table."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPITable.SeekRow
api_type:
- COM
ms.assetid: 93ac63ae-f254-45e1-a9b1-347d69d2ed9f
---

# IMAPITable::SeekRow

**Applies to**: Outlook 2013 | Outlook 2016
  
Moves the cursor to a specific position in the table.
  
```cpp
HRESULT SeekRow(
BOOKMARK bkOrigin,
LONG lRowCount,
LONG FAR * lplRowsSought
);
```

## Parameters

 _bkOrigin_
  
> [in] The bookmark identifying the starting position for the seek operation. A bookmark can be created using the [IMAPITable::CreateBookmark](imapitable-createbookmark.md) method, or one of the following predefined values can be passed.

BOOKMARK_BEGINNING
  
> Starts the seek operation from the beginning of the table.

BOOKMARK_CURRENT
  
> Starts the seek operation from the row in the table where the cursor is located.

BOOKMARK_END
  
> Starts the seek operation from the end of the table.

 _lRowCount_
  
> [in] The signed count of the number of rows to move, starting from the bookmark identified by the  _bkOrigin_ parameter.

 _lplRowsSought_
  
> [out] If  _lRowCount_ is a valid pointer on input, _lplRowsSought_ points to the number of rows that were processed in the seek operation, the sign of which indicates the direction of search, forward or backward. If  _lRowCount_ is negative, then  _lplRowsSought_ is negative.

## Return value

S_OK
  
> The seek operation was successful.

MAPI_E_BUSY
  
> Another operation is in progress that prevents the row-seeking operation from starting. Either the operation in progress should be allowed to complete or it should be stopped.

MAPI_E_INVALID_BOOKMARK
  
> The bookmark specified in the _bkOrigin_ parameter is invalid because it was removed or because it is beyond the last row requested.

MAPI_W_POSITION_CHANGED
  
> The call succeeded, but the bookmark specified in the _bkOrigin_ parameter is no longer set at the same row as it was when it was last used. If the bookmark has not been used, it is no longer in the same position as it was when it was created. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).

## Remarks

The **IMAPITable::SeekRow** method establishes a new BOOKMARK_CURRENT position for the cursor. The  _lRowCount_ parameter indicates the number of rows that the cursor moves and the direction of movement.
  
If the resulting position is beyond the last row of the table, the cursor is positioned after the last row. If the resulting position is before the first row of the table, the cursor is positioned at the beginning of the first row.
  
## Notes to implementers

If the row pointed to by  _bkOrigin_ no longer exists in the table and you cannot establish a new position for the bookmark, return MAPI_E_INVALID_BOOKMARK. If the row pointed to by_bkOrigin_no longer exists and you can establish a new position for the bookmark, return MAPI_W_POSITION_CHANGED.
  
A bookmark pointing to a row that is collapsed out of the table view can still be used. If the caller attempts to move the cursor to such a bookmark, move the cursor to the next visible row and return MAPI_W_POSITION_CHANGED.
  
You can move bookmarks for positions collapsed out of view, either at the time of use or at the time that the row is collapsed. If a bookmark is moved at the time that the row is collapsed, keep a bit in the bookmark that indicates whether the bookmark has moved since its last use or, if it has never been used, since its creation.
  
## Notes to callers

To indicate a backward move for **SeekRow**, pass a negative value in  _lRowCount_. To search to the beginning of the table, pass zero in  _lRowCount_ and the value BOOKMARK_BEGINNING in  _bkOrigin_.
  
If there are lots of rows in the table, the **SeekRow** operation can be slow. Performance can also be affected if you require a row count to be returned in the contents of the  _lplRowsSought_ parameter.
  
 **SeekRow** returns the number of rows actually searched through, positive or negative, in the variable pointed to by  _lRowCount_. In ordinary operation, it should return the same value for  _lplRowsSought_ as passed in for  _lRowCount_, unless the search reached the beginning or end of the table.
  
Do not set  _lRowCount_ to a number greater than 50. To seek through a larger number of rows, use the [IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md) method.
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProcessor.cpp  <br/> |CMAPIProcessor::ProcessMailboxTable  <br/> |MFCMAPI uses the **IMAPITable::SeekRow** method to locate the beginning of the table before processing. |

## See also

[IMAPITable::CreateBookmark](imapitable-createbookmark.md)
  
[IMAPITable::FindRow](imapitable-findrow.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
