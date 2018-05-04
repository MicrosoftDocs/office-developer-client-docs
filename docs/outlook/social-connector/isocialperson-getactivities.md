---
title: "ISocialPersonGetActivities"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cf727140-f6e7-4718-bd74-1f8feeccf70c
description: "This method has been deprecated in Outlook Social Connector 2013."
---

# ISocialPerson::GetActivities

This method has been deprecated in Outlook Social Connector 2013.
  
```
HRESULT _stdcall GetActivities([in] DATE startTime, [out, retval] BSTR* activities);
```

## Remarks

Starting in Outlook Social Connector 2013, the OSC supports only on-demand synchronization of activities and not cached or hybrid synchronization of activities. The OSC ignores the **cacheActivities** setting in the capabilities XML and does not call this method. To support dynamic activities lookup, implement the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) method. Set **cacheActivities** as **false**, **getActivities** and **dynamicActivitiesLookupEx** as **true**, which will prompt the OSC to call **ISocialSession2::GetActivitiesEx** instead. 
  
For more information about how the OSC gets friends' activities, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md). 
  
## See also

#### Reference

[ISocialPerson : IUnknown](isocialpersoniunknown.md)

