---
title: "FBUser"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium649b5400-8dc5-cc5c-3455-f462e2d31689
ms.assetid: 
description: "Identifies a user who may or may not have free/busy data available."
---

# FBUser

Identifies a user who may or may not have free/busy data available.
  
## Quick info

```cpp
typedef struct tagFBUser 
{ 
   ULONG m_cbEid; 
   LPENTRYID m_lpEid; 
   ULONG m_ulReserved; 
   LPWSTR m_pwszReserved; 
} FBUser;

```

## Members

_m_cbEid_
  
> The length of the entry ID of the mail user as represented by the [IMailUser](/previous-versions/windows/desktop/wab/-wab-imailuser-deleteprops) interface. 
    
_m_lpEid_
  
> The entry ID of the mail user as represented by the **IMailUser** interface. 
    
_m_ulReserved_
  
> This parameter is reserved for Outlook internal use and is not supported.
    
_m_pwszReserved_
  
> This parameter is reserved for Outlook internal use and is not supported.
    
## See also

- [About the Free/Busy API](about-the-free-busy-api.md)  
- [IFreeBusySupport](ifreebusysupport.md)
