---
title: "IFreeBusyDataGetFBPublishRange"
manager: soliver
ms.date: 09/23/2016
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: 1a8bbe0c-17d1-9349-4c63-f257faf4edda
description: "Gets a preset time range for an enumeration of free/busy blocks of data for a user."
---

# IFreeBusyData::GetFBPublishRange

Gets a preset time range for an enumeration of free/busy blocks of data for a user.
  
## Quick info

See [IFreeBusyData](ifreebusydata.md).
  
```cpp
HRESULT GetFBPublishRange( 
     LONG *prtmStart,  
     LONG *prtmEnd 
);

```

## Parameters

_prtmStart_
  
> [out] A relative time value for the start of free/busy information. This value is the number of minutes since January 1, 1601.
    
_prtmEnd_
  
> [out] A relative time value for the end of free/busy information. This value is the number of minutes since January 1, 1601.
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

A free/busy provider calls [IFreeBusyData::EnumBlocks](ifreebusydata-enumblocks.md) or [IFreeBusyData::SetFBRange](ifreebusydata-setfbrange.md) to set the time range for an enumeration. If either [IFreeBusyData::EnumBlocks](ifreebusydata-enumblocks.md) or [IFreeBusyData::SetFBRange](ifreebusydata-setfbrange.md) has not been called, the default values for **prtmStart** and **prtmEnd** must be set between April 1st, 1601 00:00:00Z and August 31, 4500 11:59:59Z respectively. Additionally, you should not set the start time to be greater than the end time. 
  
**IFreeBusyData::GetFBPublishRange** must return the cached values for the time range set by the most recent call for **IFreeBusyData::EnumBlocks** or **IFreeBusyData::SetFBRange**. 
  
## See also

- [Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md)
- [IFreeBusyData::EnumBlocks](ifreebusydata-enumblocks.md)
- [IFreeBusyData::SetFBRange](ifreebusydata-setfbrange.md)

