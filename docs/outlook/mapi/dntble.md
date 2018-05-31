---
title: "DNTBLE"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 10fb1650-6c3e-f467-91cd-48e5ddd82827
description: "Last modified: July 05, 2012"
---

# DNTBLE

  
  
**Applies to**: Outlook 
  
Information for downloading the contents of a folder from the server during the [download table state](download-table-state.md). This downloading process uses Microsoft Exchange Incremental Change Synchronization (ICS). For more information on ICS, see [ICS Evaluation Criteria](http://msdn.microsoft.com/en-us/library/aa579252%28EXCHG.80%29.aspx).
  
## Quick info

```cpp
struct DNTBLE 
{ 
    UINT cEntNew; 
    UINT cEntMod; 
    UINT cEntRead; 
    UINT cEntDel; 
};
```

## Members

 _cEntNew_
  
> [out] Number of items added to the local store. Outlook populates this value during the downloading when using ICS.
    
 _cEntMod_
  
> [out] Number of items modified on the local store. Outlook populates this value during the downloading when using ICS.
    
 _cEntRead_
  
> [out] Number of items read or marked unread on the local store. Outlook populates this value during the downloading when using ICS.
    
 _cEntDel_
  
> [out] Number of items deleted on the local store. Outlook populates this value during the downloading when using ICS.
    
## See also



[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[DNTBL](dntbl.md)

