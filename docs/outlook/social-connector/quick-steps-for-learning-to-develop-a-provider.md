---
title: "Quick steps for learning to develop a provider"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 13c0ae8c-d268-4bf0-942d-2a6160142f5e
description: "This topic suggests a few steps to learn about developing an Outlook Social Connector (OSC) provider."
---

# Quick steps for learning to develop a provider

To develop an OSC provider, you need to complete the following general steps:
  
- Implement the four mandatory interfaces: [ISocialProvider](isocialprovideriunknown.md), [ISocialSession](isocialsessioniunknown.md), [ISocialProfile](isocialprofileisocialperson.md), and [ISocialPerson](isocialpersoniunknown.md). Depending on your social network's support for caching logon credentials, following a person on the social network, or dynamically synchronizing friends and their activities, you might want to implement the [ISocialSession2](isocialsession2iunknown.md) interface. 
    
- In parallel with implementing interfaces, test and debug the OSC provider. 

- Deploy the OSC provider.  

- Do final testing before release.
    
## Step A: Implementing interfaces

An OSC provider implements interfaces so that the OSC can use these interfaces to obtain necessary information about or from the social network, through the OSC provider. Such information includes the following:
  
- How to present the account logon dialog to a user.    
- Whether the provider supports showing friends or activities as displayed on the social network.    
- How to display friends and activities in the Contact Card or Outlook People Pane.     
- When to refresh friends or activities information on the Contact Card or People Pane.
    
The information is typically passed from the provider to the OSC, in the form of XML strings as output parameters of interface methods. Both the OSC and an OSC provider comply with the OSC provider XML schema. Therefore, in the course of implementing the interfaces, you need a good understanding of how the XML schema allows you to specify information as listed above. 

The following resources explain how to specify XML for provider capabilities, friends, and activities:
  
- [OSC Typical Calling Sequences](osc-typical-calling-sequences.md)    
- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)    
- [Capabilities XML Example](capabilities-xml-example.md)   
- [XML for Capabilities](xml-for-capabilities.md)    
- [Friends XML Example](friends-xml-example.md)    
- [XML for Friends](xml-for-friends.md)   
- [Activity Feed XML Example](activity-feed-xml-example.md)   
- [XML for Activities](xml-for-activities.md)
    
Before you start implementation, also consult the following topics to save you time later in the debugging process:
  
- [Technical Requirements](technical-requirements.md)    
- [Best Practices for Developing a Provider](best-practices-for-developing-a-provider.md)    
- [OSC Sample Templates](osc-sample-templates.md)
    
## Step B: Debugging

The topic [Debugging a Provider](debugging-a-provider.md) suggests debugging procedures you can use while developing an OSC provider. 
  
While you are developing, you can also refer to [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md) to gain a better understanding of the expected behavior in certain scenarios (for example, basic and forms-based authentication). 
  
## Step C: Deploying

See the following topics to learn about deployment requirements:
  
- [Deploying a Provider](deploying-a-provider.md)    
- [Registering a Provider](registering-a-provider.md)   
- [Installation Checklist](installation-checklist.md)
    
## Step D: Final testing before release

Depending on your social network and the OSC provider, there are usually provider-specific tests you should carry out before you release your provider. For a suggested list of tests, see [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md).
  
## See also

- [Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)

