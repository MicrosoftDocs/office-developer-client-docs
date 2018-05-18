---
title: "OSC Typical Calling Sequences"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f61960f7-e018-4d2e-8e32-426ed46d9064
description: "This section describes the Outlook Social Connector (OSC) typical calling sequences of members in the OSC provider extensibility interfaces, which an OSC provider implements. The typical calling sequences illustrate how and when the OSC uses such interfaces and methods, to let you better determine how to implement a given member on a provider extensibility interface. The actual calling sequence can vary depending on the capabilities returned by the ISocialProvider::GetCapabilities method. Examples of capabilities include the following:"
---

# OSC Typical Calling Sequences

This section describes the Outlook Social Connector (OSC) typical calling sequences of members in the OSC provider extensibility interfaces, which an OSC provider implements. The typical calling sequences illustrate how and when the OSC uses such interfaces and methods, to let you better determine how to implement a given member on a provider extensibility interface. The actual calling sequence can vary depending on the capabilities returned by the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method. Examples of capabilities include the following: 
  
- Provider support for getting, caching, or dynamically looking up friends and activities from the social network.
    
- The user interface that the OSC should display for user logon.
    
- The authentication type (for example, forms-based authentication) that the OSC should use.
    
## In this section

[Basic Authentication](basic-authentication.md)
  
> Describes the typical calling sequence of the OSC to support an Office user who is logging on to a social network, if the OSC provider supports basic authentication.
    
[Forms-Based Authentication](forms-based-authentication.md)
  
> Describes the typical calling sequence of the OSC to support an Office user who is logging on to a social network, if the OSC provider supports forms-based authentication.
    
[Getting Activities](getting-activities.md)
  
> Describes the typical calling sequence of the OSC to synchronize the activities of the Office user's friends from a social network, if the social network OSC provider supports synchronization of activities.
    
[Getting Friends Information](getting-friends-information.md)
  
> Describes the typical calling sequence of the OSC to synchronize the Office user's friends list from a social network, if the social network OSC provider supports cached synchronization of contacts.
    
## Reference

[Outlook Social Connector Provider Reference](outlook-social-connector-provider-reference-0.md)
  
## Related sections

[Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)
  
[OSC Sample Templates](osc-sample-templates.md)
  
[Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)
  
[Debugging a Provider](debugging-a-provider.md)
  
[Deploying a Provider](deploying-a-provider.md)
  
[Best Practices for Developing a Provider](best-practices-for-developing-a-provider.md)
  
## See also



[XML for Capabilities](xml-for-capabilities.md)

