---
title: "Getting Activities"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8cb8f916-f061-4c4c-ad1b-40d44af3345a
description: "The OSC calls the ISocialProvider::GetCapabilities method to determine the capabilities of the OSC provider for a social network. If the getActivities and dynamicActivitiesLookupEx elements in the returned capabilities XML indicate that the OSC provider supports getting activities on demand and storing activities in memory, the OSC can make the following calling sequence. The OSC also notes the hash function specified in the hashFunction element in the capabilities XML. The OSC calls methods in the following sequence to get activities and information (as supported by the ISocialPerson interface) for friends and non-friends on the social network:"
---

# Getting Activities

The OSC calls the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method to determine the capabilities of the OSC provider for a social network. If the **getActivities** and **dynamicActivitiesLookupEx** elements in the returned **capabilities** XML indicate that the OSC provider supports getting activities on demand and storing activities in memory, the OSC can make the following calling sequence. The OSC also notes the hash function specified in the **hashFunction** element in the **capabilities** XML. The OSC calls methods in the following sequence to get activities and information (as supported by the [ISocialPerson](isocialpersoniunknown.md) interface) for friends and non-friends on the social network: 
  
1. [ISocialSession::GetLoggedOnUser](isocialsession-getloggedonuser.md) —At the end of the authentication process, the OSC calls **GetLoggedOnUser** to obtain an [ISocialProfile](isocialprofileisocialperson.md) interface for the user being authenticated. For more information on authentication, see [Basic Authentication](basic-authentication.md) and [Forms-Based Authentication](forms-based-authentication.md).
    
2. [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) —For the persons displayed in the Outlook People Pane, the OSC obtains and hashes their SMTP addresses, calls **ISocialSession2::GetActivitiesEx**, and stores (in memory) the activities data returned for these persons. The OSC gets in an output parameter,  _activities_, which is a string that contains a collection of activities for friends of the logged-on user. This string conforms to the schema definition for the **activityFeed** element. 
    
3. [ISocialSession::GetPerson](isocialsession-getperson.md) —For each **activityDetails** element in the **activityFeed** XML returned by **GetActivitiesEx**, there is an **ownerID** element that indicates the person who owns that activity. The OSC uses that **ownerID** value to call **GetPerson** to get an **ISocialPerson** interface for that person. 
    
4. [ISocialPerson::GetDetails](isocialperson-getdetails.md) —Based on the **ISocialPerson** object obtained from step 3, the OSC calls **GetDetails** to get details for that person, such as the first name and last name. The OSC can do the same for each activity specified in an **activityDetails** element in the **activityFeed** XML returned by **GetActivitiesEx** in step 2. 
    
> [!NOTE]
> The OSC refreshes the activities cache at a default interval. For more information about refreshing the activities cache, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md). 
  
## See also

#### Concepts

[XML for Capabilities](xml-for-capabilities.md)
#### Other resources

[OSC Typical Calling Sequences](osc-typical-calling-sequences.md)

