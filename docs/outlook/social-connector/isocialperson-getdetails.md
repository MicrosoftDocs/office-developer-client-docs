---
title: "ISocialPersonGetDetails"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9ca3172a-82a3-4483-b0aa-4e848930f6ed
description: "Gets a string that represents details for the person, such as the first name, last name, and a URL to a profile picture."
 
 
---

# ISocialPerson::GetDetails

Gets a string that represents details for the person, such as the first name, last name, and a URL to a profile picture. 
  
```
HRESULT _stdcall GetDetails([out, retval] BSTR* details);
```

## Parameters

 _details_
  
> [out] An XML string value that represents the details for a person.
    
## Remarks

The returned  _details_ XML string must comply with the schema definition for **person**, as defined in the schema for Outlook Social Connector (OSC) provider extensibility.
  
The OSC calls **GetDetails** if the OSC provider supports cached or hybrid synchronization of friends on the social network. When the OSC initially gets friends' activities for the logged on user, it calls [ISocialPerson::GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md), and stores friends' information in a contacts folder specific to the social network, in the logged on user's default Outlook store. Subsequently the OSC does not call **GetFriendsAndColleagues** or **GetDetails** unless the refresh interval for the cache has expired. For more information about how the OSC caches friends' information in a contacts folder, see [Synchronizing Friends and Activities](../../outlook-social-connector-provider-reference/developing-a-provider-with-the-osc-xml-schema/synchronizing-friends-and-activities.md).
  
## See also

#### Reference

[ISocialPerson : IUnknown](isocialpersoniunknown.md)

