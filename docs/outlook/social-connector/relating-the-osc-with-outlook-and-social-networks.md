---
title: "Relating the OSC with Outlook and social networks"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f33705cc-8add-42be-9d9f-f4e9245d83f5
description: "The Outlook Social Connector (OSC) can display in the Office Contact Card and Outlook People Pane activities, status, or photo updates for a coworker, friend, or any person you are associated with."
---

# Relating the OSC with Outlook and social networks

The Outlook Social Connector (OSC) can display in the Office Contact Card and Outlook People Pane activities, status, or photo updates for a coworker, friend, or any person you are associated with. By default, the OSC displays the Outlook emails, attachments, and meeting requests received from a selected person. If the selected person and the Office user collaborate on a SharePoint site, the OSC also displays document updates and other site activities from that SharePoint site. Depending on the contexts of association that the Office user is interested in, the Office user can install OSC providers for line-of-business applications, internal corporate websites, or a variety of professional and social network sites, such as LinkedIn, Facebook, and Windows Live.
  
To support sharing of functionality across Office client applications, the OSC core engine is implemented as part of an Office shared component, and the People Pane is implemented as an Outlook add-in. To use the OSC, an Office user must have installed Outlook on that client computer and configured Outlook with a profile, so that the OSC can cache contacts in a Contacts folder. 
  
An OSC provider is a Component Object Model (COM) DLL that allows the OSC to access social network data in a way that is independent of the APIs of each social network. An OSC provider DLL must be installed locally on a client computer. A social network's OSC provider connects the OSC, which is part of Outlook, with the social network on the Internet.
  
An OSC provider must implement a set of interfaces, defined as part of the OSC provider extensibility, to communicate with the OSC. OSC provider extensibility is available as an open platform.
  
The provider architecture of the OSC enables multiple providers to work with the OSC core engine and aggregate social information such as friends and activities. Figure 1 illustrates the OSC provider architecture.
  
**Figure 1. Outlook Social Connector provider architecture**

![Social networks, OSC providers, OSC, and Office](media/off15OSCRef_Architecture.gif)
  
## Terminology

In this Outlook Social Connector Provider Reference, a social network is used to refer to the following types of sites: 
  
- Collaborative sites such as SharePoint.
    
- Social network sites such as Facebook and Windows Live.
    
- Professional network sites such as LinkedIn.
    
- Other line-of-business applications or corporate internal websites used for networking.
    
The term friend is used generally to include friends, family, colleagues, connections, and anyone else an Office user is associated with in a collaborative context like SharePoint, or has added to the user's social network account. Non-friends are people referenced in friends' activity updates but are not friends who have been added to the Office user's social network account. Contacts are people in an Outlook contact folder. 
  
## See also

- [Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)

