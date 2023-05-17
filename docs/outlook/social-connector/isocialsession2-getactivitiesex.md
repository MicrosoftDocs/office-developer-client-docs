---
title: "ISocialSession2GetActivitiesEx"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: bfe30c22-017b-42e0-93be-c85d674c07e3
description: "Gets a string that represents a collection of activities of each of the users specified by the hashedAddresses parameter."
---

# ISocialSession2::GetActivitiesEx

Gets a string that represents a collection of activities of each of the users specified by the  _hashedAddresses_ parameter. 
  
```cpp
HRESULT _stdcall GetActivitiesEx([in] SAFEARRAY(BSTR) hashedAddresses, [in] DATE startTime, [out, retval] BSTR *activities);
```

## Parameters

_hashedAddresses_
  
> [in] A structure that specifies an array of hashed SMTP addresses for a set of users.
    
_startTime_
  
> [in] The time after which activities that are created would be returned.
    
_activities_
  
> [out] An XML string that represents the set of activities of the users specified by  _hashedAddresses_ on the social network since  _startTime_.
    
## Remarks

The OSC calls **GetActivitiesEx** if the OSC provider supports on-demand synchronization of activities. The OSC stores the information returned in  _activities_ in memory. For more information about how the OSC uses and updates this information in memory, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md).
  
Starting in Outlook Social Connector 2013, the OSC supports only on-demand synchronization of activities and calls only **GetActivitiesEx** to get activities. To support on-demand activities lookup, set **cacheActivities** as **false**, and **getActivities** and **dynamicActivitiesLookupEx** as **true**, and the OSC will call **GetActivitiesEx**.
  
The returned XML string must comply with the schema definition for **activityFeed**, as defined in the schema for OSC provider extensibility.
  
The  _hashedAddresses_ sring represents a set of hashed addresses for each user displayed in the People Pane. The hashed SMTP addresses are encrypted by using the hashing function specified by the **hashFunction** element in the provider's **capabilities** XML. The user does not have to be a friend of the logged-on user represented by the [ISocialSession::LoggedOnUserName](isocialsession-loggedonusername.md) property. 
  
The  _startTime_ parameter is a **Date** value in Coordinated Universal Time (UTC). Local time values must be converted to UTC **Date** values. 
  
Activities that the **GetActivitiesEx** method returns must have a creation time value that is greater than  _startTime_ and less than or equal to **Now**. If no changes have occurred between **startTime** and **Now**, the provider must return an OSC_E_NO_CHANGES error.
  
## See also

- [ISocialSession2 : IUnknown](isocialsession2iunknown.md)
- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)

