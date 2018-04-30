---
title: "IFreeBusyDataSetFBRange"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 4e7147ea-0eb0-324a-80d8-4f0eef654c32
description: "Sets the range of time for an enumeration of free/busy blocks of data for a user."
---

# IFreeBusyData::SetFBRange

Sets the range of time for an enumeration of free/busy blocks of data for a user.
  
## Quick Info

See [IFreeBusyData](ifreebusydata.md).
  
```
HRESULT SetFBRange(
     LONG rtmStart,
     LONG rtmEnd
);
```

## Parameters

 _rtmStart_
  
> [in] A relative time value for the start of free/busy information. This value is the number of minutes since January 1, 1601.
    
 _rtmEnd_
  
> [in] A relative time value for the end of free/busy information. This value is the number of minutes since January 1, 1601.
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

This method is used to indicate the time range of calendar items for which to retrieve details. The values of  *ftmStart*  and  *ftmEnd*  are cached and returned in a subsequent call of [IFreeBusyData::GetFBPublishRange](ifreebusydata-getfbpublishrange.md).
  
## See also

#### Concepts

[IFreeBusyData::EnumBlocks](ifreebusydata-enumblocks.md)
  
[IFreeBusyData::GetFBPublishRange](ifreebusydata-getfbpublishrange.md)
  
[How to: Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md)

