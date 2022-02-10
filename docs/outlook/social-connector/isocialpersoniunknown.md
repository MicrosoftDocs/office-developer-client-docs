---
title: "ISocialPerson  IUnknown"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 17a2fa12-a7ef-4a95-9875-72ec6f8ceac9
description: "Represents a person on the social network."
---

# ISocialPerson : IUnknown

Represents a person on the social network.
  
## Members

The following table shows the members that are available on the **ISocialPerson** interface. 
  
|**Name**|**Member type**|**Description**|
|:-----|:-----|:-----|
|[GetActivities](isocialperson-getactivities.md) <br/> |Method  <br/> |This method has been deprecated since Outlook Social Connector 2013. |
|[GetDetails](isocialperson-getdetails.md) <br/> |Method  <br/> |Gets a string that represents details for the person, such as the first name, last name, and a URL to a profile picture. |
|[GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md) <br/> |Method  <br/> |Gets a string that represents a collection of people. |
|[GetFriendsAndColleaguesIDs](isocialperson-getfriendsandcolleaguesids.md) <br/> |Method  <br/> |This method is currently not supported. |
|[GetPicture](isocialperson-getpicture.md) <br/> |Method  <br/> |Gets an array of bytes that contains the picture resource for the person. |
|[GetStatus](isocialperson-getstatus.md) <br/> |Method  <br/> |This method is currently not supported. |
   
## Remarks

An Outlook Social Connector (OSC) provider must implement this interface to communicate with the OSC.
  
## See also

- [Outlook Social Connector Provider Interfaces](outlook-social-connector-provider-interfaces.md)

