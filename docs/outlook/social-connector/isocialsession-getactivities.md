---
title: "ISocialSessionGetActivities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6546be99-aee4-41a6-8297-ace378776503
description: "This method has been deprecated in OSC 1.1."
---

# ISocialSession::GetActivities

This method has been deprecated in OSC 1.1.
  
```cpp
HRESULT GetActivities([in] SAFEARRAY(BSTR) emailAddresses, [in] DATE startTime, [out, retval] BSTR *activities);
```

## Remarks

Starting in OSC 1.1, the OSC no longer calls **GetActivities**. The OSC ignores the value of **dynamicActivitiesLookup**. To support dynamic activities lookup, implement the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) method. Set **cacheActivities** as **false**, and **getActivities** and **dynamicActivitiesLookupEx** as **true**, which will prompt the OSC to call **ISocialSession2::GetActivitiesEx** instead. 
  
## See also

- [ISocialSession : IUnknown](isocialsessioniunknown.md)

