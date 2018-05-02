---
title: "Registering a Provider"
manager: soliver
ms.date: 3/5/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: b60b3634-4c8b-4273-97a0-0a8a5a8a5342
description: "This topic describes the Windows registry locations that are used when you install an Outlook Social Connector (OSC) provider."
 
 
---

# Registering a Provider

This topic describes the Windows registry locations that are used when you install an Outlook Social Connector (OSC) provider.
  
## COM Registration

You must configure the OSC provider DLL to register using COM self-registration or regsvr32 during installation. COM registration of the provider DLL registers the OSC provider under the  `HKEY_CLASSES_ROOT` registry hive. 
  
An OSC provider developed in managed code has a COM-visible provider assembly. You should use a separate application domain for the provider component. Otherwise, the OSC provider uses the default shared application domain that is used by other components, and the provider may not operate as expected.
  
## Registering Provider ProgID

Each OSC provider must register a programmatic identifier ( `ProgID`). The provider installer can choose one of the following locations to add or remove the  `ProgID`:
  
-  `HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`—Your provider installer should use this location if the provider is installed for only the currently logged-on user.
    
-  `HKEY_LOCAL_MACHINE\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`—Your provider installer should use this location if the provider is installed for all users on the computer.
    
The OSC looks for the provider  `ProgID` in the above locations, unless the client computer has 32-bit Outlook running on a 64-bit Windows operating system. In such a case, your provider installer should choose one of the following locations in the  `HKEY_CURRENT_USER` or  `HKEY_LOCAL_MACHINE` hive: 
  
-  `HKEY_CURRENT_USER\Software\Wow6432Node\Microsoft\Office\Outlook\SocialConnector\SocialProviders`
    
-  `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Office\Outlook\SocialConnector\SocialProviders`
    
For a Click-to-Run version of Office, your provider installer should choose one of the following locations in the HKEY_CURRENT_USER or HKEY_LOCAL_MACHINE hive:
  
-  `HKEY_CURRENT_USER\Software\Microsoft\Office\ClickToRun\REGISTRY\MACHINE\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`
    
-  `HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ClickToRun\REGISTRY\MACHINE\Software\Microsoft\Outlook\SocialConnector\SocialProviders`
    
## See also

#### Concepts

[Installation Checklist](installation-checklist.md)
  
[Quick Steps for Learning to Develop a Provider](quick-steps-for-learning-to-develop-a-provider.md)
#### Other resources

[Deploying a Provider](deploying-a-provider.md)

