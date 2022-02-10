---
title: "Debugging a provider"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: d2dfaeed-7635-4c6b-9c35-b955ca1a85e9
description: "There are several ways you can debug an Outlook Social Connector (OSC) provider:"
---

# Debugging a provider

There are several ways you can debug an Outlook Social Connector (OSC) provider: 
  
- By using debug commands in the ribbon component of the Office Fluent user interface in Outlook or the supporting Office client application to cause the OSC to take various actions.
    
- By using Fiddler to trace API calls and XML sent between a social network and its OSC provider
    
## Debug buttons

The OSC provider extensibility provides the capability of debugging an OSC provider. To debug a provider, create a  `DebugProviders` value of type DWORD in the Windows registry under the  `SocialConnector` key (as shown in the following line), and set the  `DebugProviders` value to 1. 
  
`HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector`
  
By default, provider debugging is off. If the  `DebugProviders` value is not present, or it is present and set to a value of 0, provider debugging is turned off. 
  
If provider debugging is turned on, the OSC displays an alert dialog box with verbose error information when an error occurs, and validates any OSC provider XML against the OSC provider XML schema. Based on the namespace specified for an XML string, an OSC provider developed by using OSC 1.0 is validated against the OSC 1.0 schema file, OutlookSocialProvider.xsd. An OSC provider developed by using OSC 1.1 or later is validated against the schema file, OutlookSocialProvider_1.1.xsd. When you use the  `DebugProviders` value, the debug alert appears for all loaded providers instead of a specific provider. 
  
To display debug buttons that can help you debug a provider, create a  `ShowDebugButtons` value of type DWORD in the Windows registry under the  `SocialConnector` key, and set the  `ShowDebugButtons` value to 1. To hide the debug command bar buttons, set the  `ShowDebugButtons` value to 0. 
  
For Outlook 2010 and client applications since Office 2013, the debug buttons appear on the **Add-ins** tab of the explorer ribbon. For Outlook 2007 and Outlook 2003, the debug buttons appear on the standard command bar of the Outlook explorer window. 
  
The following table describes the debug buttons.
  
|**Debug button**|**Function**|
|:-----|:-----|
|Sync Contacts  <br/> |Causes the OSC to ask the OSC provider for cached contacts only. |
|GAL Sync  <br/> |Causes the OSC to populate data from the Exchange Global Address List to Outlook contacts. |
|Invalidate Category Cache  <br/> |Causes the OSC to reload the category list for each store when the activity feed is refreshed. |
   
## Fiddler

Fiddler is an over-the-wire debugging tool to check the API calls sent from your provider to the social network, and XML sent by the social network to your provider. Fiddler is available for download at [Fiddler Web Debugging Proxy](https://www.fiddler2.com/fiddler2/version.asp).
  
## See also

- [Quick Steps for Learning to Develop a Provider](quick-steps-for-learning-to-develop-a-provider.md)  
- [Synchronizing Friends and Activities](synchronizing-friends-and-activities.md) 
- [Best Practices for Developing a Provider](best-practices-for-developing-a-provider.md)
- [OSC Typical Calling Sequences](osc-typical-calling-sequences.md)  
- [Developing a Provider with the OSC XML Schema](developing-a-provider-with-the-osc-xml-schema.md)  
- [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)

