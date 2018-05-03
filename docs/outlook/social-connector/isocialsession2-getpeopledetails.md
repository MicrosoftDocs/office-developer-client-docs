---
title: "ISocialSession2GetPeopleDetails"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8733aab9-3a8e-4924-b62f-4e871d991c72
description: "Returns a string that contains a collection of person and picture details for the users specified by the personsAddresses parameter."
---

# ISocialSession2::GetPeopleDetails

Returns a string that contains a collection of person and picture details for the users specified by the  _personsAddresses_ parameter. 
  
```
HRESULT _stdcall GetPeopleDetails([in] BSTR personsAddresses, [out, retval] BSTR* personsCollection);
```

## Parameters

 _personsAddresses_
  
> [in] An XML string that specifies the hashed SMTP addresses of a set of users.
    
 _personsCollection_
  
> [out] An XML string that contains a collection of person and picture details.
    
## Remarks

The Outlook Social Connector (OSC) calls **GetPeopleDetails** if the OSC provider supports on-demand or hybrid synchronization of friends and non-friends. 
  
The  _personsAddresses_ parameter must conform to the schema definition for **hashedAddresses**, as defined in the schema for OSC provider extensibility. The  _personsAddresses_ string represents a set of hashed SMTP addresses for each user displayed in the People Pane. The user does not have to be a friend of the logged-on user represented by the [ISocialSession::LoggedOnUserName](isocialsession-loggedonusername.md) property. The hashed SMTP addresses are encrypted by using the hashing function specified by the **hashFunction** element in the provider's **capabilities** XML. The OSC identifies each **hashedAddress** in the  _personAddresses_ collection with an **index** element. The provider must use the **index** element to identify the recipient's **person** XML when it returns **friends** XML for **GetPeopleDetails**. If the recipient is not a registered user on the social network, the provider must not return any **person** XML for that recipient. The **index** element for each network user represented by **person** XML corresponds to the **index** element for the recipient in  _personsAddresses_.
  
The OSC stores the information returned by the  _personsCollection_ parameter in memory. The  _personsCollection_ XML string must conform to the schema definition for **friends**, as defined in the schema for OSC provider extensibility. For more information about how the OSC uses and updates this information in memory, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md).
  
## See also

#### Reference

[ISocialSession2 : IUnknown](isocialsession2iunknown.md)
#### Concepts

[Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)

