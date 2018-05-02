---
title: "Capabilities XML Elements"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 1951643d-e3ca-4d04-bc0c-10d9d0b35dad
description: "The tables in this topic describe child elements of the capabilities XML and are grouped by the areas they support. The default value of each capabilities element is false. If the element is not specified in the capabilities XML returned by the ISocialProvider::GetCapabilities method, the value of the element is equal to false."
 
 
---

# Capabilities XML Elements

The tables in this topic describe child elements of the **capabilities** XML and are grouped by the areas they support. The default value of each **capabilities** element is **false**. If the element is not specified in the **capabilities** XML returned by the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method, the value of the element is equal to **false**.
  
For an overview description of **capabilities** XML, see [XML for Capabilities](xml-for-capabilities.md). For an example of **capabilities** XML, see [Capabilities XML Example](capabilities-xml-example.md). For a complete definition of the Microsoft Outlook Social Connector (OSC) provider XML schema, including which elements are required or optional, see [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md).
  
## Capabilities for Supporting Friends

The following table shows elements that apply to any form of synchronization of friends or non-friends.
  
|**Element**|**Description**|
|:-----|:-----|
|**doNotFollowPerson** <br/> |Indicates whether the provider supports the [ISocialSession::UnFollowPerson](isocialsession-unfollowperson.md) method call.  <br/> **followPerson** and **doNotFollowPerson** are independent features of an OSC provider. An OSC provider can indicate the capability of being able to add a person as a friend (setting **followPerson** to **true**) or being able to remove a person as a friend on a social network account (setting **doNotFollowPerson** to **true**). In general, being able to follow does not imply being able to stop following. **followPerson** is a capability, and it is not to be misinterpreted as an action to follow a specific person or every person on the social network account. **followPerson** being **true** does not imply **doNotFollowPerson** is **false**.  <br/> |
|**followPerson** <br/> |Indicates whether the provider supports the [ISocialSession::FollowPerson](isocialsession-followperson.md) method call. The OSC checks **followPerson** if **cacheFriends** is **true** (cached synchronization of friends), **dynamicContactsLookup** is **true** (on-demand synchronization of friends and non-friends), or both **cacheFriends** and **dynamicContactsLookup** are true (hybrid synchronization of friends and non-friends). If the provider sets **followPerson** as **true**, the OSC displays a network badge in the People Pane for people that the user is following, and enables the **on \<NetworkName\>** command on the **Add (+)** menu in the People Pane. If the provider sets **followPerson** as **false**, the network badge is not displayed, and the **on \<NetworkName\>** command is hidden.  <br/> |
|**getFriends** <br/> |Indicates whether the provider supports the [ISocialPerson::GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md) or [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md) method call. If the provider sets **getFriends** as **true**, the OSC uses the value of **cacheFriends** or **dynamicContactsLookup** to determine whether the social network allows storing friends as Outlook contact items or in memory. If the provider sets **getFriends** as **false**, the social network does not support friends and the **ISocialPerson::GetFriendsAndColleagues** and **ISocialSession2::GetPeopleDetails** methods, and the OSC ignores the values of **cacheFriends** and **dynamicContactsLookup**.  <br/> |
   
The following elements apply only to cached synchronization of friends or hybrid synchronization of friends and non-friends. For more information about synchronizing friends, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md).
  
|**Element**|**Description**|
|:-----|:-----|
|**cacheFriends** <br/> |Indicates whether the OSC provider allows storing friends as Outlook contact items. The OSC checks **cacheFriends** only if **getFriends** is **true**. If the provider sets **cacheFriends** as **true**, the OSC synchronizes friends by caching, and creates a network-specific contacts folder in the user's default store for friend contacts. The name of the network-specific contacts folder is the value of the [ISocialProvider::SocialNetworkName](isocialprovider-socialnetworkname.md) property. If the provider sets **cacheFriends** as **false**, the OSC does not create a network-specific contacts folder for friend contacts to store friends.  <br/> |
|**contactSyncRestartInterval** <br/> |Determines the retry interval, in minutes, between attempts to synchronize friends' information from the social network, if a synchronization error occurs. The OSC uses this element only if the OSC provider supports cached synchronization or hybrid synchronization of friends to a social network-specific contacts folder ( **cacheFriends** is **true**).  <br/> The default retry interval is 30 minutes, unless the default is overridden by the  `ContactSyncRestartInterval` key under  `HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector`. If the provider sets **contactSyncRestartInterval**, the provider value will override the default retry interval of 30 minutes or the registry key value.  <br/> For more information about synchronizing friends and non-friends information on demand, see [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md).  <br/> |
   
The following elements apply to only on-demand synchronization or hybrid synchronization of friends and non-friends.
  
|**Element**|**Description**|
|:-----|:-----|
|**dynamicContactsLookup** <br/> |Indicates whether the OSC provider supports the [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md) call for on-demand synchronization of friends and non-friends.  <br/> The OSC checks **dynamicContactsLookup** only if **getFriends** is **true**.The default setting for **dynamicContactsLookup** is **false**.  <br/> If the OSC provider specifies **dynamicContactsLookup** as **true** and **getFriends** as **true**, the OSC calls **ISocialSession2::GetPeopleDetails** every time the People Pane is refreshed. The People Pane is refreshed when the user selects another user in the People Pane or another item in the Outlook explorer window, or opens an Outlook inspector window. Dynamic contacts lookup ensures that the user always sees the latest user pictures and profile information in the People Pane, but increases the number of calls from the provider to the social network.  <br/> If the provider sets **dynamicContactsLookup** as **false**, the OSC does not call **ISocialSession2::GetPeopleDetails** to refresh the People Pane.  <br/> |
|**showOnDemandContactsWhenMinimized** <br/> |Indicates if the OSC should carry out on-demand synchronization for friends and non-friends when the People Pane is minimized.  <br/> |
   
## Capabilities for Supporting Activities

The following element applies to any form of synchronization of activities supported by the OSC provider.
  
|**Element**|**Description**|
|:-----|:-----|
|**getActivities** <br/> |Indicates whether the provider supports the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) or [ISocialPerson::GetActivities](isocialperson-getactivities.md) method calls. If the provider sets **getActivities** as **true**, the OSC uses the value of **cacheActivities** or **dynamicActivitiesLookupEx** to determine whether the social network site allows storing activities as Outlook RSS items or as in-memory activities. If the provider sets **getActivities** as **false**, the social network does not support activities and the **ISocialSession2::GetActivitiesEx** and **ISocialPerson::GetActivities** methods, and the OSC ignores the values of **cacheActivities** and **dynamicActivitiesLookupEx**.  <br/> |
   
The following element applies to only cached synchronization or hybrid synchronization of activities.
  
|**Element**|**Description**|
|:-----|:-----|
|**cacheActivities** <br/> |Starting in Outlook Social Connector 2013, the OSC ignores this element since providers can no longer synchronize activities by caching them in a hidden folder in the user's store.  <br/> If the provider supports activities, the provider must support synchronize activities on-demand. The provider sets **cacheActivities** as **false** and sets **dynamicActivitesLookupEx** as **true**. The OSC synchronizes activities on-demand, and caches activities in memory. The activities memory cache is refreshed on a 30-minute interval.  <br/> |
   
The following elements apply to only on-demand synchronization or hybrid synchronization of activities.
  
|**Element**|**Description**|
|:-----|:-----|
|**dynamicActivitiesLookup** <br/> |Deprecated in OSC 1.1.  <br/> Starting in OSC 1.1, the OSC no longer calls [ISocialSession::GetActivities](isocialsession-getactivities.md) and ignores the value of **dynamicActivitiesLookup**. To support on-demand activities lookup, set **cacheActivities** as **false** and **getActivities** and **dynamicActivitiesLookupEx** as **true**, and the OSC will call **ISocialSession2::GetActivitiesEx**.  <br/> |
|**dynamicActivitiesLookupEx** <br/> |Indicates whether the OSC provider supports the **ISocialSession2::GetActivitiesEx** call for on-demand synchronization of activities.  <br/> If the OSC provider supports on-demand activities synchronization, it sets **getActivities** and **dynamicActivitiesLookupEx** as **true**, and **cacheActivities** as **false**. The OSC calls **ISocialSession2::GetActivitiesEx** every time the People Pane is refreshed. The People Pane is refreshed when the user changes the selected item in the Outlook explorer window or opens an Outlook inspector window. Dynamic activities lookup ensures that the user will always see the latest activities in the People Pane, but will increase the number of calls from the provider to the social network.  <br/> If the provider sets **dynamicActivitiesLookupEx** as **false**, the OSC does not call **ISocialSession2::GetActivitiesEx** for people displayed in the People Pane.  <br/> |
|**showOnDemandActivitiesWhenMinimized** <br/> |Indicates whether the OSC should carry out on-demand synchronization for activities when the People Pane is minimized.  <br/> |
   
## Common Capabilities for Supporting On-Demand or Hybrid Synchronization of Friends, Non-Friends, and Activities

|**Element**|**Description**|
|:-----|:-----|
|**hashFunction** <br/> | Specifies the hash function that the OSC provider supports. To protect personally identifiable information of users who are not on the provider's social network or line-of-business application, the OSC passes hashed email addresses to **ISocialSession2::GetPeopleDetails** and **ISocialSession2::GetActivitiesEx**.  <br/>  If **dynamicContactsLookup** is set to **true** or **dynamicActivitiesLookupEx** is set to **true**, the provider must set **hashFunction** to one of the allowed values: **SHA1**, **MD5**, or **CRC32MD5**. If **hashFunction** is missing or specifies an incorrect value, the OSC returns an error.  <br/> **SHA1** is Internet Engineering Task Force (IETF) US Secure Hash Algorithm 1 defined by [[RFC3174]](http://www.rfc-editor.org/rfc/rfc3174.txt). For example, the **SHA1** hashed value of email address melissa@contoso.com is  `bb81577b567262a21a4df5f6e335c1250acd7b50`.  <br/> **MD5** is Internet Engineering Task Force (IETF) MD5 Message-Digest Algorithm defined by [[RFC1321]](http://www.rfc-editor.org/rfc/rfc1321.txt). For example, the **MD5** hashed value of e-mail address melissa@contoso.com is  `c8c39e61ca1662477b39b83d7b0a0615`.  <br/> **CRC32MD5** is a combination of **CRC32** and **MD5** defined as follows:  <br/>  Normalize the email address by removing leading and trailing whitespace and converting all characters to lowercase.  <br/>  Compute the **CRC32** value for the normalized email address and use the decimal integer representation of this value. If your implementation returns signed integers, you must convert the signed integer to an unsigned integer.  <br/>  Compute the **MD5** value for the normalized email address and use the hex representation of this value (using lowercase for A through F).  <br/>  Combine these two values with an underscore.  <br/>  For example, the **CRC32MD5** hashed value of email address melissa@contoso.com is  `2149665315_c8c39e61ca1662477b39b83d7b0a0615`.  <br/> |
   
## Capabilities for Supporting Authentication and Account Configuration

|**Element**|**Description**|
|:-----|:-----|
|**allowChangesToAutoConfigure** <br/> |Indicates whether the social network allows the user to change auto-configuration settings, such as providing a different URL to log on.  <br/> |
|**createAccountUrl** <br/> |If the provider sets **hideHyperlinks** as **false**, when the user clicks **Click here to create an account** in the **Account configuration** dialog box, the URL specified by **createAccountUrl** opens in the default browser.  <br/> |
|**displayUrl** <br/> |Indicates whether the OSC should display the **URL Address** text box for the social network in the account configuration dialog box.  <br/> |
|**forgotPasswordUrl** <br/> |If the provider sets **hideHyperlinks** as **false**, when the user clicks **Forgot your password?** in the **Account configuration** dialog box, the URL specified by **forgotPasswordUrl** opens in the default browser.  <br/> |
|**hideHyperlinks** <br/> |Indicates whether the OSC should hide the **Click here to create an account** and **Forgot your password?** hyperlinks in the account configuration dialog box.  <br/> OSC 1.0 ignores this setting, and the hyperlinks are always hidden. OSC 1.1 observes the value of this setting.  <br/> |
|**hideRememberMyPassword** <br/> |Indicates whether the OSC should hide the **Remember my password** check box in the account configuration dialog box.  <br/> If the provider sets **hideRememberMyPassword** as **true**, the OSC will act as if the **Remember my password** box is unchecked and will not save the password.  <br/> If the provider sets **hideRememberMyPassword** as **false**, the OSC will display the **Remember my password** check box in the account configuration dialog box.  <br/> |
|**supportsAutoConfigure** <br/> |Indicates whether the OSC should call the **GetAutoConfiguredSession** function on the **ISocialProvider** interface to attempt automatic configuration and log on to the social network for the user.  <br/> |
|**useLogonCached** <br/> |Indicates whether the OSC provider supports the [ISocialSession2::LogonCached](isocialsession2-logoncached.md) call to log on with cached credentials.  <br/> If the provider sets **useLogonCached** as **true**, the OSC ignores the setting for **useLogonWebAuth** and the OSC calls **ISocialSession2::LogonCached** for authentication.  <br/> If the provider sets **dynamicActivitiesLookupEx** as **false**, the OSC does not call **ISocialSession2::LogonCached** for authentication.  <br/> |
|**useLogonWebAuth** <br/> |Indicates whether the OSC should use forms-based authentication and the [ISocialSession::LogonWeb](isocialsession-logonweb.md) method. If the provider sets **useLogonWebAuth** as **false**, the OSC uses basic authentication and calls the [ISocialSession::Logon](isocialsession-logon.md) method. If the provider sets **useLogonWebAuth** as **true**, the OSC uses forms-based authentication and calls **ISocialSession::LogonWeb**.  <br/> |
   
Depending on the **capabilities** XML returned by the provider in the **ISocialProvider::GetCapabilities** method, the account configuration dialog box changes. For example, Figure 1 shows the account configuration dialog box for a TestProvider example. 
  
**Figure 1. TestProvider example in the account configuration dialog box**

![TestProvider example configuration information](media/odc_ol14_ta_OSCFigure4.jpg)
  
## See also

#### Concepts

[XML for Capabilities](xml-for-capabilities.md)

