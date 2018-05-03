---
title: "ISocialPersonGetFriendsAndColleagues"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 62d5b815-f199-499e-85eb-2dff21a8216e
description: "Gets a string that represents a collection of people."
---

# ISocialPerson::GetFriendsAndColleagues

Gets a string that represents a collection of people.
  
```
HRESULT _stdcall GetFriendsAndColleagues([out, retval] BSTR* personsCollection);
```

## Parameters

 _personsCollection_
  
> [out] An XML string that represents a set of friends of the person, and that complies with the definition of **friends** as defined in the XML schema for Outlook Social Connector (OSC) provider extensibility. 
    
## Remarks

The OSC calls **GetFriendsAndColleagues** if the OSC provider supports cached or hybrid synchronization of friends on the social network. When the OSC initially calls the **GetFriendsAndColleagues** method for the Outlook user who is logged on to the social network, **GetFriendsAndColleagues** returns an XML string that represents friends of the logged-on user on the social network. The XML string complies with the **friends** XML schema definition and specifies a **person** element (which also complies with the OSC provider schema definition) for each friend. 
  
When **GetFriendsAndColleagues** returns the friends information for the logged-on user, the OSC stores that information in a contacts folder. This folder is specific to the social network and resides in the logged-on user's default Outlook store. For more information about how the OSC caches friends' information in a contacts folder, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md).
  
Information for each friend returned in the  _personsCollection_ parameter complies with the XML schema definition for **person**. The **person** element supports many pieces of information for each friend, including the SMTP email addresses (which map to the **emailAddress**, **emailAddress2**, and **emailAddress3** elements) that the friend has specified on the social network, and the user ID (which maps to the **userID** element) that identifies that friend on the social network. 
  
To show activities for an Outlook user selected in the People Pane, the OSC tries to match the user with each friend returned from **GetFriendsAndColleagues**. The OSC does this by matching the SMTP address of the selected Outlook user with the email addresses that each friend has specified on the social network. If the OSC finds a matching SMTP email address, the OSC uses the corresponding **userID** of the friend to call the [ISocialSession::GetPerson](isocialsession-getperson.md) method. It does this to obtain an [ISocialPerson](isocialpersoniunknown.md) object for that friend, which then enables the OSC to get activities and pictures of that friend from the social network. 
  
However, if the selected Outlook user does not specify that same SMTP address on an account on the social network, or if the Outlook user does not have an account on that social network, the OSC will not be able to find a match for that user and will not display any activities for that user on the social network.
  
## See also

#### Reference

[ISocialPerson : IUnknown](isocialpersoniunknown.md)
#### Concepts

[Getting Friends Information](getting-friends-information.md)

