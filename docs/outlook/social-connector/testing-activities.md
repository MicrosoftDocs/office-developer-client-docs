---
title: "Testing Activities"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 98343c36-5e32-4d07-b474-adfeca693135
description: "This topic describes tests and scenarios to verify that the Outlook Social Connector (OSC) provider uses on-demand synchronization to appropriately return activities of friends and non-friends."
---

# Testing Activities

This topic describes tests and scenarios to verify that the Outlook Social Connector (OSC) provider uses on-demand synchronization to appropriately return activities of friends and non-friends.
  
## On-Demand Synchronization
<a name="olosc_TestingActivities_OnDemandSync"> </a>

An OSC provider implements **ISocialProvider::GetCapabilities**, which the OSC calls to determine whether the provider supports on-demand synchronization of activities of friends and non-friends. For the persons displayed in the Outlook People Pane, the OSC obtains and hashes their SMTP addresses, calls [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md), and stores (in memory) the activities data returned for these persons. 
  
### Determining Activities to Get

The hashed SMTP addresses passed to **GetActivitiesEx** are the key to determining whether the OSC will get activities for a friend or non-friend. The OSC gets activities for a person if the person specifies that SMTP address in his or her social network account. If the person does not include that SMTP address in his or her social network account, or if that person is a friend but by a different email address on the social network, **GetActivitiesEx** does not get activities for that person. Also, for a person who is not a friend but specifies the SMTP addresses in his or her social network account, the data returned includes only what is available to a non-friend as allowed by the privacy settings of that person. 
  
### Creating Test Subjects for Friends and Non-Friends

To create a test subject for a friend, identify the SMTP address of a person who includes that address in his or her social network account and who has a friend status with the logged-on user on that network. Create an email message that includes that SMTP address. Similarly, to create a test subject for a non-friend, identify the SMTP address of a person who is not a friend of the logged-on user by that address, and who has specified in his or her privacy settings to allow non-friends to view their profile on the social network. Create an email message that includes that SMTP address. 
  
In the Outlook explorer, when you select the email message that includes a friend (or non-friend), the People Pane displays the recipients. Selecting the friend (or non-friend) in the People Pane allows you to test that the provider is providing information about the person.
  
### Test Scenarios

To verify that you are getting appropriate activities for friends and non-friends, test for the following scenarios.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Person selected in the People Pane is a friend with the logged-on user on the social network.  <br/> |The People Pane displays that person's profile and profile picture as posted on the social network.  <br/> |
|Person selected in the People Pane is a non-friend of the logged-on user on the social network, but has allowed his or her profile to be viewed by non-friends.  <br/> |The People Pane displays that person's profile and profile picture as posted on the social network.  <br/> |
   
## See also
<a name="olosc_TestingActivities_OnDemandSync"> </a>



[Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)
  
[XML for Activities](xml-for-activities.md)


[Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)

