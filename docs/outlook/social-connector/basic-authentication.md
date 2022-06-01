---
title: "Basic authentication"
description: "Describes the calling sequence that the Outlook Social Connector can make to allow a user to log on to a social network."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 89349d1e-365a-442e-9ba3-2df601d9323c
---

# Basic authentication

The Outlook Social Connector (OSC) calls the [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) method to determine the capabilities of the OSC provider for a social network. The OSC uses the returned capabilities to determine how to support an Office user who is logging on to this social network. If the **useLogonWebAuth** element in the returned **capabilities** XML indicates that the OSC provider supports basic authentication, the OSC can make the following calling sequence to allow a user to log on to that social network: 
  
1. [ISocialProvider::Load](isocialprovider-load.md) —The OSC loads the provider. 
    
2. [ISocialProvider::Version](isocialprovider-version.md) —The OSC gets a string that represents the version number of the OSC provider. 
    
3. [ISocialProvider::SocialNetworkName](isocialprovider-socialnetworkname.md) —The OSC gets a string that represents the social network name. 
    
4. [ISocialProvider::SocialNetworkGuid](isocialprovider-socialnetworkguid.md) —The OSC gets an immutable GUID that represents the social network. 
    
5. [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md) —The OSC gets a string that represents the provider's capabilities and that complies with the schema definition for the **capabilities** element. 
    
6. [ISocialProvider::SocialNetworkIcon](isocialprovider-socialnetworkicon.md) —The OSC gets a byte array that represents the icon for the social network site. 
    
7. [ISocialProvider::GetSession](isocialprovider-getsession.md) —The OSC gets an [ISocialSession](isocialsessioniunknown.md) interface. 
    
8. [ISocialSession::Logon](isocialsession-logon.md) —The OSC logs the user on to the social network site by using the specified user name and password. 
    
9. [ISocialSession::GetLoggedOnUser](isocialsession-getloggedonuser.md) —The OSC gets an [ISocialProfile](isocialprovideriunknown.md) interface that represents the logged-on user. 
    
10. [ISocialSession::GetNetworkIdentifier](isocialsession-getnetworkidentifier.md) —The OSC gets a string that represents a unique identifier for a social network site. The network identifier can be equivalent to the network name. 
    
## See also

- [XML for Capabilities](xml-for-capabilities.md)
- [OSC Typical Calling Sequences](osc-typical-calling-sequences.md)

