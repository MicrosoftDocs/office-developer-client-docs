---
title: "ISocialProfileGetActivitiesOfFriendsAndColleagues"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4aaf7417-0a03-42a4-a282-599327ec5381
description: "This method has been deprecated in Outlook Social Connector 2013."
---

# ISocialProfile::GetActivitiesOfFriendsAndColleagues

This method has been deprecated in Outlook Social Connector 2013.
  
```
HRESULT _stdcall GetActivitiesOfFriendsAndColleagues([in] DATE startTime, [out, retval] BSTR* activitiesCollection);
```

## Remarks

Starting in Outlook Social Connector 2013, the OSC supports only on-demand synchronization of activities and not cached or hybrid synchronization of activities. The OSC ignores the **cacheActivities** setting in the capabilities XML and no longer calls this method. To support dynamic activities lookup, implement the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) method. Set **getActivities** and **dynamicActivitiesLookupEx** as **true**, which will prompt the OSC to call **ISocialSession2::GetActivitiesEx** instead. 
  
For more information about how the OSC gets friends' activities, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md). 
  
## See also

#### Reference

[ISocialProfile : ISocialPerson](isocialprofileisocialperson.md)

