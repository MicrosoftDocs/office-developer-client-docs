---
title: "Testing Following and Stop-Following Persons"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c603c3c6-62c8-4895-93e1-b2e146dfaa4f
description: "This topic describes scenarios to test the Outlook Social Connector (OSC) provider's ability to follow a friend, and to stop following a friend on the social network."
---

# Testing Following and Stop-Following Persons

This topic describes scenarios to test the Outlook Social Connector (OSC) provider's ability to follow a friend, and to stop following a friend on the social network.
  
## Following a Person

To follow a person is to add a person as a friend on the social network, using the SMTP address provided by the selected Outlook item. Following someone on a social network usually involves requesting permission from that person by an email to that SMTP address. In order to grant permission, that person must either have that SMTP address already included in his or her social network account, or be willing to add that SMTP to a social network account. Test each of the following scenarios to verify that your OSC provider behaves correctly.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Attempting to follow a person on the social network who exists on the social network.  <br/> |For a social network that does not require permission from the person, the social network immediately adds the person as a friend.  <br/> For a network that requires permission from that person, the social network sends a notification. The Outlook People Pane displays a pending icon for that person.  <br/> |
|Attempting to follow a person on the social network who does not exist on the social network.  <br/> |The OSC provider displays the appropriate error in [ISocialSession::FollowPerson](isocialsession-followperson.md) or [ISocialSession2::FollowPersonEx](isocialsession2-followpersonex.md).  <br/> |
|Following a friend on the social network.  <br/> |For the friend selected in the People Pane, the social network's badge and the friend's profile picture for that social network are displayed.  <br/> |
|Selecting the link to the profile page of a friend.  <br/> |The friend's page on the social network opens in the logged-on user's default browser.  <br/> |
   
## Stop Following a Person

To stop following a person is to remove that person as a friend on the social network. Test the following scenario to verify your OSC provider stops following a person properly.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Attempting to remove a person as a friend on the social network.  <br/> |The social network no longer lists that person as a friend on the logged on user's account.  <br/> |
   
## See also

#### Other resources

[Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)

