---
title: "Synchronizing friends and activities"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 6e91b765-a207-4d8c-8763-5d643ca4d0c0
description: "The Outlook Social Connector (OSC) supports displaying information from a social network about a person in the Contact Card or in the Outlook People Pane. SharePoint Server, SharePoint Workspace, Lync client, and all Office client applications that support presence information support the Contact Card."
---

# Synchronizing friends and activities

The Outlook Social Connector (OSC) supports displaying information from a social network about a person in the Contact Card or in the Outlook People Pane. SharePoint Server, SharePoint Workspace, Lync client, and all Office client applications that support presence information support the Contact Card.
  
You can use the Contact Card in collaboration scenarios in Office applications to find out more about the people you're collaborating with. Examples of these scenarios include messaging in Outlook and co-authoring a document in Word. When you click the **What's new** tab of a Contact Card, the displays information about that person. 
  
The Outlook People Pane displays information about a person who can be a sender or recipient of an Outlook item you have selected. Whenever you select another person in the People Pane or another item in the Outlook explorer, or open an Outlook item in an inspector, the Outlook Social Connector (OSC) refreshes the People Pane. 
  
For the Contact Card or People Pane to display current information for the selected person, the OSC synchronizes such information through the OSC providers and some form of caching. This synchronization depends on the OSC providers that are installed on the client computer, the social networks that you have logged onto through their OSC providers, and the synchronization mode that each of the OSC providers for these social networks supports.
  
The OSC supports synchronizing friends, non-friends, and activities for friends and non-friends in different ways: cached synchronization, on-demand synchronization, and hybrid synchronization. The main difference among these modes of synchronization is where the OSC stores the data—whether it is in a folder in the user's default Outlook store, or in memory on the user's computer. In each case as noted in this topic, there is a default minimum time that the data remains in the folder or memory before the data is refreshed. In some cases, the minimum amount of time can be customized by group policy. For more information about group policies that control the behavior of the OSC, see [How to manage the Outlook Social Connector by using Group Policy](https://support.microsoft.com/default.aspx?scid=kb%3Ben-US%3B2020103).
  
Note that if the selected person is not a member of the social network, the OSC does not display any person or activity information for that person in the Contact Card or People Pane.
  
## Cached synchronization

An OSC provider can store information for friends on the social network in a specific folder on the user's default Outlook store, and periodically update that cache after a specified length of time has expired. Caching information in a folder has the advantage of reducing traffic to the social network.
  
> [!NOTE]
> Starting in Outlook Social Connector 2013, the OSC no longer supports cached synchronization of activities. 
  
### Cached synchronization of friends

If an OSC provider supports cached synchronization for friends, the OSC caches information for friends of the logged-on user on the social network. The information is cached in an Outlook contacts folder that's specific to that social network in the user's default Outlook store. The contacts folder name is based on the name of the social network, which the OSC obtains by using the [ISocialProvider::SocialNetworkName](isocialprovider-socialnetworkname.md) property. 
  
In cached synchronization, the OSC stores information for only the logged-on user's friends on the social network. The OSC does not access information for non-friends.
  
The default interval for the OSC to refresh the contacts folder for friends' information from the social network is once per day (or once per 1440 minutes). This refresh interval can also be set by group policy, as discussed at the beginning of this topic.
  
If an error occurs during a refresh, the OSC retries at an interval that is specified by the **contactSyncRestartInterval** element in the **capabilities** XML. This retry interval has a default value of 30 minutes, and can also be set by group policy. 
  
When a user opens a Contact Card and selects the **What's new** tab, the **What's new** tab refreshes. Similarly, when an Outlook user reselects an item in Outlook or reselects a person on the People Pane, the People Pane refreshes. If the cache refresh interval has not expired, the OSC goes to the cache to obtain any information for the selected user. This avoids the overhead of using OSC provider extensibility to access the social network. If the refresh interval has expired, the OSC calls the [ISocialPerson::GetFriendsAndColleagues](isocialperson-getfriendsandcolleagues.md) method to get current friends' information for the logged-on user, and updates the cache in the contacts folder. 
  
The OSC provider informs the OSC that it supports cached synchronization of friends by specifying the following elements in the **capabilities** XML: 
  
- **getFriends** = **true**
    
- **cacheFriends** = **true**
    
- **dynamicContactsLookup** = **false**
    
## On-demand synchronization

When a user selects the **What's new** tab in a Contact Card, or selects a different Outlook item or a different person in the People Pane in Outlook, the OSC refreshes the Contact Card or People Pane respectively. If an OSC provider supports on-demand synchronization of persons or activities, the OSC synchronizes with a cache in memory, and updates details, such as name, title, picture, and activity streams, on the Contact Card or People Pane. For on-demand synchronization, unlike cached synchronization, the OSC attempts to refresh the information for the person regardless of whether that person is a friend or non-friend of the logged-on user on the social network. 
  
On-demand person (or activity) data is stored in memory only. The in-memory data is cleared when the Office client application shuts down, or the user causes a refresh of the Contact Card or People Pane and the data has remained in memory for longer than the refresh interval. Note that the refresh from the social network is always initiated by a user refreshing the Contact Card or People Pane, (for example, by selecting a different user in the People Pane, or selecting a different item in Outlook explorer window). 

However, the reverse is not always true—not every refresh of the Contact Card or People Pane necessarily incurs a refresh from the social network. If the user refreshes the Contact Card or People Pane, and the person (or activity) data has remained in memory for longer than the refresh interval, the OSC calls [ISocialSession2::GetPeopleDetails](isocialsession2-getpeopledetails.md) (or [ISocialSession2::GetActivitiesEx](isocialsession2-getactivitiesex.md)) to update the information in memory from the social network. The allowed period for friend and non-friend information in memory is 24 hours, and for activities, 30 minutes. 
  
One important difference between cached and on-demand synchronization is that on-demand synchronization can fetch person and activity information for both friends and non-friends on the network. If the selected person is a non-friend, the OSC refreshes information and activities for that person if either of the following requirements is met: 
  
- The person is a user on the social network and allows public viewing of profile and activity information.
    
- The person is in the same network as the logged-on user on that social network (for example, in the same network for university alumni).
    
On-demand synchronization of persons and activities results in more calls to the provider from the OSC core engine. Social networks must be able to handle the increased bandwidth requirements of on-demand synchronization.
  
### Specifying XML elements for on-demand synchronization

The OSC provider informs the OSC that it supports on-demand synchronization of friends and non-friends by specifying the following elements in the **capabilities** XML: 
  
- **getFriends** = **true**
    
- **cacheFriends** = **false**
    
- **dynamicContactsLookup** = **true**
    
The OSC provider informs the OSC that it supports on-demand synchronization of activities by specifying the following elements in the **capabilities** XML: 
  
- **getActivities** = **true**
    
- **cacheActivities** = **false**
    
- **dynamicActivitiesLookupEx** = **true**
    
## Hybrid synchronization

An OSC provider can support hybrid synchronization of friends and non-friends. This can optimize the calls between the OSC core engine and the OSC provider, the calls to the social network for on-demand synchronization of friends, and the currency of the friends' data. The minimum time the data can remain in a folder or memory, where applicable, is the same as the limits in cached or on-demand synchronization modes.
  
> [!NOTE]
> Starting in Outlook Social Connector 2013, the OSC supports only on-demand synchronization of activities and no longer supports hybrid synchronization of activities. 
  
### Hybrid synchronization of friends and non-friends

If an OSC provider supports hybrid synchronization of friends and non-friends, the OSC does the following: 
  
- The OSC stores information for friends of the logged-on user in the social network-specific contact folder.
    
- The OSC stores information for non-friends of the logged-on user in memory.
    
The OSC provider informs the OSC that it supports hybrid synchronization of friends and non-friends by specifying the following elements in the **capabilities** XML: 
  
- **getFriends** = **true**
    
- **cacheFriends** = **true**
    
- **dynamicContactsLookup** = **true**
    
## Synchronization intervals

The following table summarizes the synchronization intervals for friends and non-friends information between the corresponding cache (folder or memory) and the social network, depending on the supported synchronization mode. For hybrid synchronization mode, refer to the rows for cached mode for friends, and the row for on-demand mode for non-friends.
  
|**Synchronization mode for persons**|**Where refresh interval is set**|**Default minimum time before refresh**|**Group policy override**|
|:-----|:-----|:-----|:-----|
|Cached  <br/> |Set within OSC  <br/> |1440 minutes (24 hours)  <br/> |Windows registry value **NetContactSyncInterval** <br/> |
|Cached  <br/> |**contactSyncRestartInterval** element in **capabilities** XML  <br/> |30 minutes if **contactSyncRestartInterval** is not set  <br/> |Windows registry value **contactSyncRestartInterval** <br/> |
|On-demand  <br/> |Set within OSC  <br/> |1440 minutes (24 hours)  <br/> |Windows registry value **OnlineSearchExpiryTime** <br/> |
   
The following table summarizes the synchronization intervals for activities of friends and non-friends between the corresponding cache (folder or memory) and the social network, depending on the supported synchronization modes. 
  
|**Synchronization mode for activities**|**Where refresh interval is set**|**Default minimum time before refresh**|**Group policy override**|
|:-----|:-----|:-----|:-----|
|On-demand  <br/> |Set within OSC  <br/> |30 minutes  <br/> |Windows registry value **OnlineSearchExpiryTime** <br/> |
   
The following information applies to the Windows registry values listed in the two tables:
  
- Key:  `HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\Outlook\SocialConnector`
    
- Value: DWORD value between 1 and 10080
    
## See also

- [Capabilities XML Example](capabilities-xml-example.md)  
- [XML for Capabilities](xml-for-capabilities.md)
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)  
- [How to manage the Outlook Social Connector by using Group Policy](https://support.microsoft.com/default.aspx?scid=kb%3Ben-US%3B2020103)

