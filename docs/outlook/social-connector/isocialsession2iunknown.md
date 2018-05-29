---
title: "ISocialSession2  IUnknown"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f516e86e-0158-472b-9711-fe7491b24404
description: "Supports adding friends, on-demand or hybrid synchronization of friends, on-demand synchronization of activities, or logging on to the social network by using cached credentials."
---

# ISocialSession2 : IUnknown

Supports adding friends, on-demand or hybrid synchronization of friends, on-demand synchronization of activities, or logging on to the social network by using cached credentials.
  
## Members

The following table shows the members that are available on the **ISocialSession2** interface. 
  
|**Name**|**Member type**|**Description**|
|:-----|:-----|:-----|
|[FollowPersonEx](isocialsession2-followpersonex.md) <br/> |Method  <br/> |Adds the person identified by the  _emailAddresses_ and  _displayName_ parameters as a friend for the logged-on user on the social network.  <br/> |
|[GetActivitiesEx](isocialsession2-getactivitiesex.md) <br/> |Method  <br/> |Gets a string that represents a collection of activities of the users specified by the  _hashedAddresses_ parameter.  <br/> |
|[GetPeopleDetails](isocialsession2-getpeopledetails.md) <br/> |Method  <br/> |Returns a string that contains a collection of person and picture details for the users specified by the  _personsAddresses_ parameter.  <br/> |
|[LogonCached](isocialsession2-logoncached.md) <br/> |Method  <br/> |Logs on to the social network site using cached credentials.  <br/> |
   
## Remarks

An Outlook Social Connector (OSC) provider can choose to implement this interface if the provider supports on-demand or hybrid synchronization of friends, on-demand synchronization of activities, or logging on to the social network by using cached credentials. If the OSC provider implements **ISocialSession2** and supports following persons on the social network, the OSC would call [ISocialSession2::FollowPersonEx](isocialsession2-followpersonex.md) instead of [ISocialSession::FollowPerson](isocialsession-followperson.md), and the provider must implement **ISocialSession2::FollowPersonEx**, as well.
  
## See also

- [Outlook Social Connector Provider Interfaces](outlook-social-connector-provider-interfaces.md)

