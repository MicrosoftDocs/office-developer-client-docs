---
title: "Capabilities XML example"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: ae1abafe-160c-47c0-b4d5-4a689c8c4cb1
description: "The XML example in this topic is an XML string returned to the Outlook Social Connector (OSC) after it calls the ISocialProvider::GetCapabilities method for a social network. The XML shows how an OSC provider specifies its capabilities and requirements for the OSC."
---

# Capabilities XML example

The XML example in this topic is an XML string returned to the Outlook Social Connector (OSC) after it calls the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method for a social network. The XML shows how an OSC provider specifies its capabilities and requirements for the OSC. 
  
## Capabilities for friends

In this example, the OSC provider specifies the following elements to show its capabilities in supporting the friends feature:
  
- **getFriends** as **true** to indicate the OSC provider supports the [ISocialPerson::GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md) method to get friends' information programmatically. 
    
- **cacheFriends** as **true** to support caching friends' information in an Outlook contacts folder. 
    
- **contactSyncRestartInterval** as 60 to indicate that on error, the OSC should retry refreshing the cache every 60 minutes. 
    
- **followPerson** as **true** to indicate the ability to add friends on the social network. 
    
- **doNotFollowPerson** as **false** to indicate the OSC provider does not support removing a person as a friend on the social network. 
    
- **dynamicContactsLookup** as **false** to indicate that the OSC should not store friends' information in memory. 
    
## Capabilities for activities

The OSC provider specifies the following elements to show its capability to support activities:
  
- **getActivities** as **true** to indicate that the OSC provider supports the [ISocialProfile::GetActivitiesOfFriendsAndColleagues](isocialprofile-getactivitiesoffriendsandcolleagues.md) method to get friends' activities programmatically. 
    
- **cacheActivities** as **false** to support caching activities of friends in the hidden Outlook News Feed folder. 
    
- **dynamicActivitiesLookupEx** as **true** to indicate that the OSC should store friends' activities in memory. 
    
## Capabilities for authentication and account configuration

The OSC provider specifies the following elements to show its support for authentication and account configuration:
  
- **useLogonWebAuth** as **false** to indicate that the OSC provider supports basic authentication. 
    
- **supportsAutoConfigure** as **false** to indicate that the OSC should not attempt to automatically configure and log on to the social network for the user. 
    
- **useLogonCached** and **hideRememberMyPassword** as **false** to indicate that the OSC should prompt for password every time and should not use cached logon credentials to log on. 
    
- **displayUrl** as **false** to indicate that the OSC should not display the URL for the social network in the account configuration dialog box. 
    
- **hideHyperlinks** as **false** to indicate that the OSC provider supports only existing accounts with known passwords, and the OSC should not display the **Click here to create an account** and **Forgot your password?** hyperlinks in the account configuration dialog box. 
    
## XML example

The following example shows the **capabilities** XML of an OSC provider. 
  
```XML
<?xml version="1.0" encoding="utf-8" ?>
<capabilities xmlns="http://schemas.microsoft.com/office/outlook/2010/06/socialprovider.xsd">
  <getFriends>true</getFriends>
  <cacheFriends>true</cacheFriends>
  <followPerson>true</followPerson>
  <doNotFollowPerson>false</doNotFollowPerson>
  <getActivities>true</getActivities>
  <cacheActivities>false</cacheActivities>
  <displayUrl>false</displayUrl>
  <useLogonWebAuth>false</useLogonWebAuth>
  <hideHyperlinks>false</hideHyperlinks>
  <supportsAutoConfigure>false</supportsAutoConfigure>
  <contactSyncRestartInterval>60</contactSyncRestartInterval>
  <dynamicActivitiesLookupEx>true</dynamicActivitiesLookupEx>
  <dynamicContactsLookup>false</dynamicContactsLookup>
  <useLogonCached>false</useLogonCached>
  <hideRememberMyPassword>false</hideRememberMyPassword>
  <createAccountUrl>https://contoso.com/createAccount</createAccountUrl>
  <forgotPasswordUrl>https://contoso.com/forgotPassword</forgotPasswordUrl>
</capabilities>

```

## See also

- [OSC Provider XML Examples](osc-provider-xml-examples.md)  
- [XML for Capabilities](xml-for-capabilities.md)  
- [Friends XML Example](friends-xml-example.md)  
- [Activity Feed XML Example](activity-feed-xml-example.md)  
- [Outlook Social Connector Provider XML Schema](outlook-social-connector-provider-xml-schema.md)

