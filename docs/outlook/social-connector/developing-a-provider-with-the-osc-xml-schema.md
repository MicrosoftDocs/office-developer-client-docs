---
title: "Developing a Provider with the OSC XML Schema"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0872b1b9-c21f-4bba-8cf1-4b010d8d7fb6
description: "The Outlook Social Connector (OSC) provider XML schema defines the format of a significant amount of information that is passed from a social network through the network's OSC provider to the OSC. The XML schema allows an OSC provider to specify capabilities of the provider, friends, and activity feed items on the social network, by using the three main elements, capabilities, friends, and activityFeed, and their child elements. The OSC provider implements interfaces and their methods in the OSC provider extensibility, returning XML strings as output parameters that comply with the OSC provider XML schema. The OSC calls these methods to obtain information that it can understand as defined by the XML schema."
---

# Developing a Provider with the OSC XML Schema

The Outlook Social Connector (OSC) provider XML schema defines the format of a significant amount of information that is passed from a social network through the network's OSC provider to the OSC. The XML schema allows an OSC provider to specify capabilities of the provider, friends, and activity feed items on the social network, by using the three main elements, **capabilities**, **friends**, and **activityFeed**, and their child elements. The OSC provider implements interfaces and their methods in the OSC provider extensibility, returning XML strings as output parameters that comply with the OSC provider XML schema. The OSC calls these methods to obtain information that it can understand as defined by the XML schema.
  
> [!NOTE]
> OSC provider extensibility supports debugging providers by setting the  `DebugProviders` value of the  `HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector` registry key to 1. When you turn on provider debugging, the OSC validates the provider XML against the version of the OSC XML schema that you specify in the **xmlns** XML attribute. For OSC 1.1 and versions of the OSC since Outlook Social Connector 2013, specify the **xmlns** attribute as follows: >  `xmlns="http://schemas.microsoft.com/office/outlook/2010/06/socialprovider.xsd"`
  
## In this section

[Synchronizing Friends and Activities](synchronizing-friends-and-activities.md)
  
> Describes the various ways that OSC providers can synchronize friends, non-friends, and activities on a social network. 
    
[OSC Provider XML Examples](osc-provider-xml-examples.md)
  
> Includes XML examples that show how to specify capabilities of an OSC provider, friends, and activity feed items on a social network by using the OSC XML schema.
    
[XML for Capabilities](xml-for-capabilities.md)
  
> Explains the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method that the OSC uses to obtain capabilities information, expressed in **capabilities** XML, from the OSC provider. This section also describes the XML elements in the OSC provider XML schema that allow an OSC provider to specify its functionality, including how it authenticates users and synchronizes friends and activities. 
    
[XML for Friends](xml-for-friends.md)
  
> Gives examples of the APIs that the OSC uses to obtain friends' information, expressed in **friends** XML, from the OSC provider. This section also describes elements in the **friends** XML. 
    
[XML for Activities](xml-for-activities.md)
  
> Gives examples of the APIs that the OSC uses to obtain activities information, expressed in **activityFeed** XML, from the OSC provider. This section also describes the XML elements in the OSC provider XML schema that allow an OSC provider to specify an activity feed. An activity feed includes the network where the activity feed items originated, details of each activity feed item (such as owner, type, and publish date of the activity), and the template to display the activity. 
    
## Reference

[Outlook Social Connector Provider Reference](outlook-social-connector-provider-reference-0.md)
  
## Related sections

[Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)
  
[OSC Sample Templates](osc-sample-templates.md)
  
[OSC Typical Calling Sequences](osc-typical-calling-sequences.md)
  
[Debugging a Provider](debugging-a-provider.md)
  
[Deploying a Provider](deploying-a-provider.md)
  
[Best Practices for Developing a Provider](best-practices-for-developing-a-provider.md)
  
## See also

#### Concepts

[Debugging a Provider](debugging-a-provider.md)

