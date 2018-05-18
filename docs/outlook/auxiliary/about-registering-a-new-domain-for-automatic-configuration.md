---
title: "About registering a new domain for automatic configuration"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: a7ab8a50-dd30-4ba5-b6d8-e6d1f482e6f1
description: "Outlook provides a way to specify a new message service domain for automatic configuration and allow the message service provider to configure the account."
---

# About registering a new domain for automatic configuration

Outlook provides a way to specify a new message service domain for automatic configuration and allow the message service provider to configure the account.
  
When designing a message service provider, you can use the following key in the Windows registry to specify a new domain to be automatically configured by the corresponding message service provider: 
  
 `HKLM\Software\Microsoft\Office\Outlook\AutoConfigDomains\<domain name>\`
  
In the key,  `<domain name>` is the domain for automatic configuration. This domain name supports a wildcard \* at the beginning only. The following table shows the values that this key supports. 
  
|**Value**|**Type**|**Description**|
|:-----|:-----|:-----|
|Friendly Name  <br/> |REG_SZ  <br/> |The domain name that is displayed to the user during automatic configuration.  <br/> |
|Service Name  <br/> |REG_SZ  <br/> |The message service registered in mapisvc.inf that supports this domain.  <br/> |
|Install Location  <br/> |REG_SZ  <br/> |The URL of the location to install the message service provider, if it is not already installed.  <br/> |
|Minimum Version  <br/> |REG_DWORD  <br/> |The minimum version of the .dll of the message service provider that is required. This value is optional.  <br/> |
   
When Outlook begins automatic configuration for an email account, it checks the Windows registry for the registration of the domain specified by the email address. If the domain is already specified in the Windows registry, Outlook checks whether the message service is registered in Mapisvc.inf. Outlook cannot proceed with automatic configuration of the domain unless it has been specified in the Windows registry.
  
If the specified message service is not currently registered in Mapisvc.inf, or the message service provider is installed but the .dll has a version earlier than the specified minimum, Outlook uses the specified friendly name and prompts the user to install the provider. If the user accepts, Outlook redirects the user to the specified installation location so that the user can install the provider. Installing the provider registers the message service in Mapisvc.inf.
  
If the message service is currently registered in Mapisvc.inf and the service provider .dll is an appropriate version, Outlook creates the message service by using [IMsgServiceAdmin::CreateMsgService](http://msdn.microsoft.com/library/0135f049-0311-45e5-9685-78597d599a4e%28Office.15%29.aspx), and then configures it by using [IMsgServiceAdmin::ConfigureMsgService](http://msdn.microsoft.com/library/a08f5905-2585-49ca-abb7-a77f2736f604%28Office.15%29.aspx). Outlook automatic configuration uses the following three properties to allow the provider to set up the account: [PidTagAutoConfigurationUserName](http://msdn.microsoft.com/library/05dfa0e2-4ab1-4f57-9009-6a815aca87bd%28Office.15%29.aspx), [PidTagAutoConfigurationUserEmail](http://msdn.microsoft.com/library/845140c8-5454-4b47-acec-ab5aff00b768%28Office.15%29.aspx), and [PidTagAutoConfigurationUserPassword](http://msdn.microsoft.com/library/d33e7c45-55d8-4dc1-ade9-605542d87e61%28Office.15%29.aspx).
  
## See also



[File Format of MapiSvc.inf](http://msdn.microsoft.com/library/b48eda17-83a8-4dc4-85c8-4ca827d13d25%28Office.15%29.aspx)

