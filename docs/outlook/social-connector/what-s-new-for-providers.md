---
title: "What's new for providers"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 92f59a0d-3834-424d-ad81-167fdeba9bd0
description: "This topic lists the major changes in Outlook Social Connector 2013 (OSC). It presents a comparison of the features available between Outlook Social Connector 2013 and Outlook Social Connector 1.1."
---

# What's new for providers

This topic lists the major changes in Outlook Social Connector 2013 (OSC). It presents a comparison of the features available between Outlook Social Connector 2013 and Outlook Social Connector 1.1. It also describes interface members and XML elements that have been added, changed, or deprecated. 
  
In Office 2013, the OSC works with not only Outlook, but also SharePoint Server, SharePoint Workspace, Lync client, and all other Office client applications that support presence information and the Contact Card. An OSC provider can surface social information updates in the **WHAT'S NEW** tab in the Outlook People Pane, as well as in the Contact Card. 
  
A few major changes in Outlook Social Connector 2013 include the following: 
  
- If a provider supports showing activities, the provider always synchronizes activities on demand and no longer relies on previously cached activities. That means the provider stores activities of friends and non-friends in memory to display more current activities.
    
- For security reasons, providers that communicate with servers over the Internet should use the HTTPS (Hypertext Transfer Protocol (HTTP) with Secure Socket Layer (SSL)) protocol. Otherwise, there is a risk that email addresses, social network activities and other user data is intercepted or exposed while in transit.
    
- If you have providers that work with an earlier version of Outlook, to support Office 2013, you should update the setup package. See [Installation Checklist](installation-checklist.md) for more information. 
    
The following table shows the availability of various features in Outlook Social Connector 2013 as compared with Outlook Social Connector 1.1.
  
|**Feature**|**Outlook Social Connector 2013**|**Outlook Social Connector 1.1**|
|:-----|:-----|:-----|
|End user interface  <br/> |SharePoint Server, SharePoint Workspace, Lync client, Contact Card in all Office client applications, and People Pane in Outlook  <br/> |People Pane in Outlook  <br/> |
|Basic authentication  <br/> |Yes  <br/> |Yes  <br/> |
|Forms-based authentication  <br/> |Yes  <br/> |Yes  <br/> |
|Cached authentication  <br/> |Yes  <br/> |Yes  <br/> |
|Cached sync for friends to contacts folder on default store  <br/> |Yes  <br/> |Yes  <br/> |
|Cached activities sync for friends to hidden **Newsfeed** folder  <br/> |No  <br/> |Yes  <br/> |
|On-demand sync (picture, name, title) for friends and non-friends on network  <br/> |Yes  <br/> |Yes  <br/> |
|On-demand activities sync for friends and non-friends on network  <br/> |Yes  <br/> |Yes  <br/> |
|Follow on network  <br/> |Yes  <br/> |Yes  <br/> |
|Do not follow on network  <br/> |Yes  <br/> |Yes  <br/> |
|Visit user profile page  <br/> |Via a link  <br/> |Via a network badge  <br/> |
|Observing privacy settings on social network (for example, displaying profile and activities of non-friends who allow viewing of such)  <br/> |Yes  <br/> |Yes  <br/> |
|Hashed email addresses passed to provider  <br/> |Yes  <br/> |Yes  <br/> |

<a name="OlSocialConnector_Changes"> </a>

## Changes from the previous version of OSC provider extensibility

The following table shows the members that have been added or deprecated from the corresponding interface.
  
|**Interface and member**|**Comment**|
|:-----|:-----|
|**ISocialProfile::GetActivitiesOfFriendsAndColleagues** <br/> |Deprecated in Outlook Social Connector 2013. Note that **ISocialSession::GetActivities** has also been deprecated since Outlook Social Connector 1.1.  <br/> To synchronize activity feeds, you should implement the [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md) method. Set **dynamicActivitiesLookupEx** as **true**, which will prompt the OSC to call **ISocialSession2::GetActivitiesEx** instead.  <br/> |
   
The following table shows the schema elements that have changed.
  
|**Schema element**|**Comment**|
|:-----|:-----|
|**capabilities** <br/> |Added in Outlook Social Connector 2013: **allowChangesToAutoConfigure** element.  <br/> Deprecated in Outlook Social Connector 2013: **cacheActivities** element.  <br/> |
|**person** <br/> |Added in Outlook Social Connector 2013: **askmeabout**, **businessAddress**, **businessCity**, **businessCountryOrRegion**, **businessState**, **businessZip**, **industries**, **interests**, **location**, **otherAddress**, **otherCity**, **otherCountryOrRegion**, **otherState**, **otherZip**, **skills**, **schools**, and **website** elements.  <br/> |
   
## See also

- [XML for Capabilities](xml-for-capabilities.md)
- [XML for Friends](xml-for-friends.md)
- [Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)

