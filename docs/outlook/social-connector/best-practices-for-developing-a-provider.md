---
title: "Best Practices for Developing a Provider"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 22e3de8a-c4f2-41a4-a5b1-c5b1bf06f724
description: "You should adhere to the following practices when you develop an Outlook Social Connector 2013 (OSC) provider:"
---

# Best Practices for Developing a Provider

You should adhere to the following practices when you develop an Outlook Social Connector 2013 (OSC) provider:
  
- For security reasons, providers that communicate with servers over the Internet should use the HTTPS (Hypertext Transfer Protocol (HTTP) with Secure Socket Layer (SSL)) protocol. Otherwise, there is a risk that email addresses, social network activities, and other user data could be intercepted or exposed while in transit.
    
- If you are developing an OSC provider for a third-party social network, your provider must adhere to the social network's terms of service.
    
- To minimize the size of the provider download package, build the provider by using a native compiler such as C++ or any other tool that can build a COM component.
    
- In your provider, create a unique user agent that is sent to the social network to track calls made by the provider to the social network.
    
- The [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method should not rely on calling the social network over the Internet to get the capabilities of the provider. For example, users can start Outlook offline; if the OSC calls **GetCapabilities** and there is no network connection, the **GetCapabilities** call will not return valid **capabilities** XML. The best practice is to store **capabilities** XML as a resource in your provider. 
    
- Your OSC provider can generate a significant volume of calls to a social network. Depending on the terms of service for your social network, consider caching friends to an Outlook folder to reduce the number of calls from the OSC to your provider and, in turn, from your provider to the social network.
    
- Office 2013 is available in both 32-bit and 64-bit versions. Versions of Office prior to Office 2010 are available only in a 32-bit version. The default installation of Office 2013 on 64-bit Windows is 32-bit. If you intend to support the 64-bit version of the OSC that is installed with 64-bit Office 2013, you must also release a 64-bit version of your provider. 
    
## See also

#### Other resources

[OSC Typical Calling Sequences](osc-typical-calling-sequences.md)
  
[Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)
  
[Deploying a Provider](deploying-a-provider.md)
  
[Getting Started with Developing an Outlook Social Connector Provider](getting-started-with-developing-an-outlook-social-connector-provider.md)

