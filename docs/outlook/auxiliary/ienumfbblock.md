---
title: "IEnumFBBlock"
manager: lindalu
ms.date: 12/08/2015
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: fad9c0fd-b523-db98-ee0d-78aad5914ff2
---

# IEnumFBBlock

Supports accessing and enumerating free/busy blocks of data for a user within a time range.
  
## Quick info

|Property |Value |
|:-----|:-----|
|Inherits from:  <br/> |[IUnknown](https://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx) <br/> |
|Provided by:  <br/> |Free/busy provider  <br/> |
|Interface identifier:  <br/> |**IEnumFBBlock** <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[Next](ienumfbblock-next.md) <br/> |Gets the next specified number of blocks of free/busy data in an enumeration. |
|[Skip](ienumfbblock-skip.md) <br/> |Skips a specified number of blocks of free/busy data. |
|[Reset](ienumfbblock-reset.md) <br/> |Resets the enumerator by setting the cursor to the beginning. |
|[Clone](ienumfbblock-clone.md) <br/> |Creates a copy of the enumerator, using the same time restriction but setting the cursor to the beginning of the enumerator. |
|[Restrict](ienumfbblock-restrict.md) <br/> |Restricts the enumeration to a specified time period. |
   
## Remarks

An enumeration contains free/busy blocks of data that do not overlap in time. When there are overlapping items on a calendar, Outlook merges these items to form non-overlapping free/busy blocks in the enumeration based on this order of precedence: out-of-office, busy, tentative.
  
A free/busy provider obtains this interface and the enumeration for a time range for a user through [IFreeBusyData](ifreebusydata.md).
  
## See also

- [About the Free/Busy API](about-the-free-busy-api.md)  
- [Constants (Free/busy API)](constants-free-busy-api.md)  
- [IFreeBusyData](ifreebusydata.md)

