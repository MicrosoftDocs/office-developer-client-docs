---
title: "Testing friends"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 109c34b6-911b-4dfc-9799-aadf47172e84
description: "This topic describes tests and scenarios to verify that the Outlook Social Connector (OSC) provider appropriately returns data of friends and non-friends, where applicable, depending on the synchronization mode supported by the provider."
---

# Testing friends

This topic describes tests and scenarios to verify that the Outlook Social Connector (OSC) provider appropriately returns data of friends and non-friends, where applicable, depending on the synchronization mode supported by the provider.

<a name="olosc_TestingFriends_CachedSync"> </a>

## Cached synchronization

An OSC provider implements [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md), which the OSC calls to determine whether the provider supports cached synchronization of friends' data. After calling [ISocialPerson::GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md), the OSC stores the returned friends' data in a contacts folder specific to the social network in the logged-on user's default Outlook store. The OSC also calls [ISocialSession::GetPerson](isocialsession-getperson.md) and [ISocialPerson::GetPicture](isocialperson-getpicture.md) to obtain a profile picture for each friend. 
  
### Initiate synchronization

To initiate synchronization, you can turn on and use the debug button **Sync Contacts** in the ribbon component of the Microsoft Office Fluent user interface. For more information about OSC debug buttons, see [Debugging a Provider](debugging-a-provider.md). 
  
### Test scenarios

Test the following items to verify that friends' data is cached correctly.
  
|**Item to test**|**Expected behavior**|
|:-----|:-----|
|Contacts folder  <br/> |The social network-specific contacts folder exists in the user's default Outlook store. |
|Friends' data returned by **ISocialPerson::GetFriendsAndColleagues** <br/> |Each friend corresponds to a contact in the network-specific contacts folder. |
|Friends' data  <br/> |Contact fields for each friend have the correct data. |
|Friends' profile pictures returned by **ISocialPerson::GetPicture** <br/> |The contact item for each friend contains the profile picture. |

<a name="olosc_TestingFriends_OnDemandSync"> </a>

## On-demand synchronization

An OSC provider implements **ISocialProvider::GetCapabilities**, which the OSC calls to determine whether the provider supports on-demand synchronization of friends and non-friends. For the persons displayed in the Outlook People Pane, the OSC obtains and hashes their SMTP addresses, calls [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md), and stores (in memory) the data returned for these persons. 
  
### Determining friends and non-friends

The hashed SMTP addresses passed to **GetPeopleDetails** are the key to determining whether a person is a friend or non-friend. If a person does not include that SMTP address in his or her social network account, or even if that person is a friend by a different email address on the social network, **GetPeopleDetails** still returns **nonfriend** for that person as the **friendStatus** in the _personsCollection_ parameter. Also, for a person who is not a friend but specifies the SMTP address in his or her social network account, the data returned includes only what is available to a non-friend as allowed by the privacy settings of that person. 
  
### Creating test subjects for friends and non-friends

To create a test subject for a friend, identify the SMTP address of a person who includes that address in his or her social network account and who has a friend status with the logged-on user on that network. Create an email message that includes that SMTP address. Similarly, to create a test subject for a non-friend, identify the SMTP address of a person who is not a friend of the logged-on user by that address, and yet who has specified in his or her privacy settings to allow non-friends to view their activities on the social network. Create an email message that includes that SMTP address. 
  
In the Outlook explorer, when you select the email message that includes a friend (or non-friend), the People Pane displays the recipients. Selecting the friend (or non-friend) in the People Pane allows you to test that the provider is providing information about the person.
  
### Test scenarios

To verify that your provider is providing information about friends and non-friends appropriately, test for the following scenarios.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Person selected in the People Pane is a friend with the logged-on user on the social network. |The People Pane displays that person's activities on the social network. |
|Person selected in the People Pane is a non-friend of the logged-on user on the social network, but has allowed his or her activities to be viewed by non-friends. |The People Pane displays that person's activities on the social network. |

<a name="olosc_TestingFriends_OnDemandSync"> </a>

## Hybrid synchronization

If an OSC provider supports hybrid synchronization of friends and non-friends, the OSC does the following: 
  
- The OSC stores information for friends of the logged-on user in the social network-specific contact folder.
    
- The OSC retrieves information for non-friends on-demand from the social network, and stores it only in memory, but not in a folder.
    
To test hybrid synchronization, follow the testing suggestions in the [Cached Synchronization](#olosc_TestingFriends_CachedSync) section for friends, and those in the [On-Demand Synchronization](#olosc_TestingFriends_OnDemandSync) section for non-friends. 
  
## See also

- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md) 
- [XML for Friends](xml-for-friends.md)
- [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)

