---
title: "Forms-Based Authentication"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 282b2377-45ba-4f0c-a7d9-830fa3505c93
description: "The Outlook Social Connector (OSC) calls the ISocialProvider::GetCapabilities method to determine the capabilities of the OSC provider for a social network. The OSC uses the returned capabilities to determine how to support an Office user who is logging on to this social network. If the useLogonWebAuth element in the returned capabilities XML indicates that the OSC provider supports forms-based authentication, the OSC can make the following calling sequence to allow a user to log on to that social network:"
 
 
---

# Forms-Based Authentication

The Outlook Social Connector (OSC) calls the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method to determine the capabilities of the OSC provider for a social network. The OSC uses the returned capabilities to determine how to support an Office user who is logging on to this social network. If the **useLogonWebAuth** element in the returned **capabilities** XML indicates that the OSC provider supports forms-based authentication, the OSC can make the following calling sequence to allow a user to log on to that social network: 
  
1. [ISocialProvider::Load](isocialprovider-load.md) —The OSC loads the provider. 
    
2. [ISocialProvider::Version](isocialprovider-version.md) —The OSC gets a string that represents the version number of the provider for this social network. 
    
3. [ISocialProvider::SocialNetworkName](isocialprovider-socialnetworkname.md) —The OSC gets a string that represents the social network name. 
    
4. [ISocialProvider::SocialNetworkGuid](isocialprovider-socialnetworkguid.md) —The OSC gets an immutable GUID that represents the social network. 
    
5. [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) —The OSC gets a string that represents the provider's capabilities and that complies with the schema definition for the **capabilities** element. 
    
6. [ISocialProvider::SocialNetworkIcon](isocialprovider-socialnetworkicon.md) —The OSC gets a byte array that represents the icon for the social network site. 
    
7. [ISocialProvider::GetSession](isocialprovider-getsession.md) —The OSC gets an [ISocialSession](isocialsessioniunknown.md) interface. 
    
8. [ISocialSession::LogonWeb](isocialsession-logonweb.md) —The OSC initializes logging on to the social network site by forms-based authentication. For this initial logon call, the OSC passes **null** for the  _connectIn_ parameter. 
    
9. [ISocialSession::GetLogonUrl](isocialsession-getlogonurl.md) —The OSC gets the URL to display a browser-based form to the user during web authentication. 
    
10. [ISocialSession::LogonWeb](isocialsession-logonweb.md) —The OSC completes the logon to the social network site by using forms-based authentication. The OSC calls this method a second time, passing the URL of the logon form to the provider in the  _connectIn_ parameter. 
    
11. [ISocialSession::GetLoggedOnUser](isocialsession-getloggedonuser.md) —The OSC gets an [ISocialProfile](isocialprovideriunknown.md) interface that represents the logged-on user. 
    
12. [ISocialSession::GetNetworkIdentifier](isocialsession-getnetworkidentifier.md) —The OSC gets a string that represents a unique identifier for a social network site. The network identifier can be equivalent to the network name. 
    
## See also

#### Concepts

[XML for Capabilities](xml-for-capabilities.md)
#### Other resources

[OSC Typical Calling Sequences](osc-typical-calling-sequences.md)

