---
title: "IFreeBusySupportLoadFreeBusyData"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: f0baa310-7a53-07ee-0a7d-33dd1fb465c2
description: "Returns, for each specified user, an interface for enumerating free/busy blocks of data within a time range."
 
 
---

# IFreeBusySupport::LoadFreeBusyData

Returns, for each specified user, an interface for enumerating free/busy blocks of data within a time range. 
  
## Quick Info

See [IFreeBusySupport](ifreebusysupport.md).
  
```
HRESULT LoadFreeBusyData( 
    ULONG cMax,  
    FBUser *rgfbuser, 
    IFreeBusyData **prgfbdata,  
    HRESULT *phrStatus, 
    ULONG *pcRead 
);
```

## Parameters

 _cMax_
  
> [in] The number of [IFreeBusyData](ifreebusydata.md) interfaces to return. 
    
 _rgfbuser_
  
> [in] The array of free/busy users to retrieve data for.
    
 _prgfbdata_
  
> [in][out] The array of **IFreeBusyData** interfaces that correspond to the  _rgfbuser_ array of [FBUser](fbuser.md) structures. 
    
    > [!NOTE]
    > This array of pointers is allocated by the caller and freed by the caller. The actual interfaces pointed to are released when the caller is done with them. 
  
 _phrStatus_
  
> [out] The array of **HRESULT** results for retrieving each corresponding **IFreeBusyData** interface. The value may be NULL. A result is set to S_OK if corresponding  _prgfbdata_ is valid. 
    
 _pcRead_
  
>  [out] The actual number of users for which an **IFreeBusyData** interface has been found. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

#### Concepts

[Constants (Free/busy API)](constants-free-busy-api.md)

