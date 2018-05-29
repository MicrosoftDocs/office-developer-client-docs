---
title: "IFreeBusyDataEnumBlocks"
manager: soliver
ms.date: 2/18/2016
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 0cd5a5ae-118f-c7da-4eda-e97590fc39d4
description: "Gets an interface that enumerates free/busy blocks of data for a user within a specified time range."
---

# IFreeBusyData::EnumBlocks

Gets an interface that enumerates free/busy blocks of data for a user within a specified time range.
  
## Quick info

See [IFreeBusyData](ifreebusydata.md).
  
```cpp
HRESULT EnumBlocks( 
     IEnumFBBlock **ppenumfb,  
     FILETIME ftmStart, 
     FILETIME ftmEnd 
);

```

## Parameters

_ppenumfb_
  
> [out] An interface to enumerate free/busy blocks.
    
_ftmStart_
  
> [in] The start time for the enumeration. It is expressed in [FILETIME](http://msdn.microsoft.com/library/ 4af8e79a-697e-44a1-8576-fdc57726e9ef.aspx).
    
_ftmEnd_
  
> [in] The end time for the enumeration. It is expressed in **FILETIME**. 
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

This method is used to indicate the time range of calendar items for which to retrieve details. The values of  *ftmStart* and *ftmEnd* are cached and returned in a subsequent call of [IFreeBusyData::GetFBPublishRange](ifreebusydata-getfbpublishrange.md).
  
A free/busy provider can also subsequently use the returned [IEnumFBBlock](ienumfbblock.md) interface to access the enumeration. 
  
## See also

- [IEnumFBBlock](ienumfbblock.md)
- [IFreeBusyData::GetFBPublishRange](ifreebusydata-getfbpublishrange.md)
- [IFreeBusyData::SetFBRange](ifreebusydata-setfbrange.md)
- [Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md)

