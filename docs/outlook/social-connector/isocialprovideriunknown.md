---
title: "ISocialProvider  IUnknown"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 1c9f4dd4-65f6-446f-8b86-a375ce402658
description: "Represents an instance of an Outlook Social Connector (OSC) provider."
---

# ISocialProvider : IUnknown

Represents an instance of an Outlook Social Connector (OSC) provider.
  
## Members

The following table shows the members that are available on the **ISocialProvider** interface. 
  
|**Name**|**Member type**|**Description**|
|:-----|:-----|:-----|
|[DefaultSiteUrls](isocialprovider-defaultsiteurls.md) <br/> |Property  <br/> |Returns an array of strings that specify site URLs for the OSC provider.  <br/> |
|[GetAutoConfiguredSession](isocialprovider-getautoconfiguredsession.md) <br/> |Method  <br/> |Gets an automatically configured [ISocialSession](isocialsessioniunknown.md) interface.  <br/> |
|[GetCapabilities](isocialprovider-getcapabilities.md) <br/> |Method  <br/> |Gets a string that describes provider capabilities.  <br/> |
|[GetSession](isocialprovider-getsession.md) <br/> |Method  <br/> |Gets an [ISocialSession](isocialsessioniunknown.md) interface.  <br/> |
|[GetStatusSettings](isocialprovider-getstatussettings.md) <br/> |Method  <br/> |This method is currently not supported.  <br/> |
|[Load](isocialprovider-load.md) <br/> |Method  <br/> |Initializes the OSC provider.  <br/> |
|[SocialNetworkGuid](isocialprovider-socialnetworkguid.md) <br/> |Property  <br/> |Returns a GUID that represents a unique identifier for the social network.  <br/> |
|[SocialNetworkIcon](isocialprovider-socialnetworkicon.md) <br/> |Property  <br/> |Returns an array of bytes that represents the icon for the social network.  <br/> |
|[SocialNetworkName](isocialprovider-socialnetworkname.md) <br/> |Property  <br/> |Returns a string that represents the social network name.  <br/> |
|[Version](isocialprovider-version.md) <br/> |Property  <br/> |Returns a string that represents the version number of the provider for this social network.  <br/> |
   
## Remarks

An OSC provider must implement this interface to communicate with the OSC.
  
## See also

- [Outlook Social Connector Provider Interfaces](outlook-social-connector-provider-interfaces.md)

