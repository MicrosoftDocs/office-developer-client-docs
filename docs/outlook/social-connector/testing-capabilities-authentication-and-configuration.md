---
title: "Testing capabilities, authentication, and configuration"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 69e1f5bc-354c-4c33-84a1-b1aa10d4b650
description: "This topic describes tests for getting capabilities, and scenarios around configuring an account and authenticating a user for a social network."
---

# Testing capabilities, authentication, and configuration

This topic describes tests for getting capabilities, and scenarios around configuring an account and authenticating a user for a social network.
  
## Getting capabilities

A Outlook Social Connector (OSC) provider implements [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md), and the OSC calls **GetCapabilities** to get the functionality supported by the provider. The capabilities that your provider supports for your social network should be known at the point of implementation, and should not depend on a call to the social network in real time. For example, Outlook users can start Outlook offline, and **GetCapabilities** cannot rely on network connectivity at the time when Outlook starts. 
  
When testing the provider, you should verify that the  _results_ string parameter returned by **GetCapabilities** conforms to the **capabilities** element as defined by the OSC provider XML schema. For more information, see [Capabilities XML Elements](capabilities-xml-elements.md).
  
## Configuring an account

When the OSC configures an account, you should verify whether the social network icon and name are displayed, and that the create-account and forgot-password hyperlinks appear in the account configuration dialog box as specified by the provider.
  
### Social network icon and name

After getting capabilities, the OSC can proceed to get the icon and name for the social network by calling [ISocialProvider::SocialNetworkIcon](isocialprovider-socialnetworkicon.md) and [ISocialProvider::SocialNetworkName](isocialprovider-socialnetworkname.md). Do the following tests to verify that these method calls succeed.
  
|**Item to test**|**Expected behavior**|
|:-----|:-----|
|Social network icon  <br/> | The social network icon is displayed correctly in the following places in the OSC:  <br/>  In the OSC dialog box for **Social Network Accounts**.  In the drop-down menu when you attempt to add a person as a friend.  In the badge when following a friend. <br/>**NOTE**:  You can access the dialog box for **Social Network Accounts** by clicking the **View** tab in Outlook, in the **People Pane** group, clicking **People Pane**, and then clicking **Account Settings**.           |
|Social network name  <br/> | The social network name is displayed correctly in the following places in the OSC:  <br/>  In the OSC dialog box for **Social Network Accounts**.  In the drop-down menu when you attempt to add a person as a friend.  As the title of the password dialog box when you attempt to change the existing password. |
   
### Showing hyperlinks in configuration dialog

After calling **ISocialProvider::GetCapabilities**, the OSC uses the value of the **hideHyperlinks** element in the _results_ parameter to determine whether to hide or display the **Click here to create an account** and **Forgot your password?** hyperlinks in the account configuration dialog box. Verify that if **hideHyperlinks** is **false**, the account configuration displays these URLs.
  
### Support to create account

Verify that if the _results_ parameter from the **ISocialProvider::GetCapabilities** method call has the **hideHyperlinks** element set to **false** and the **createAccountUrl** element set to **true**, clicking the URL opens the page in the default web browser.
  
### Support for forgotten password

Verify that if the _results_ parameter from the **ISocialProvider::GetCapabilities** method call has the **hideHyperlinks** element set to **false** and the **forgotPasswordUrl** element set to **true**, clicking the URL opens the page in the default web browser.
  
## Authenticating users

Test for the following scenarios regardless of whether your OSC provider supports basic authentication or forms-based authentication.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|Logging on for the first time. |The user can successfully log on to the social network. |
|Logging on with a password made up of a variety of characters, including punctuation and Unicode characters. |The user can successfully log on to the social network, independent of the kind of characters used in the password. |
|The dialog box for **Social Network Accounts** displaying the user name or ID. |After the user has successfully logged on to the network, the OSC's dialog box for **Social Network Accounts** displays the logged-on user name or ID. |
|Authentication fails. |The OSC displays the error **Invalid user name or password**. |
|Cannot connect to the social network. |The OSC displays the error **Server cannot be found**. |
|Being able to retrieve items. |Once the user has authenticated, all activity should be allowed. There are no errors getting friends' data or activities. |
|Logging on to the social network after restarting Outlook. |If the OSC provider allows caching of the password, after the user has authenticated the first time, the user is not subsequently prompted for credentials whenever the OSC attempts to get data from the social network. |
   
In addition, if your OSC provider supports forms-based authentication, test for the following scenario as well.
  
|**Scenario**|**Expected behavior**|
|:-----|:-----|
|The OSC getting a URL to a form for the user to log on from calling [ISocialSession::GetLogonUrl](isocialsession-getlogonurl.md). |The OSC opens the URL in the user's default browser, and the webpage allows the user to enter credentials to log on to the social network. |
   
## See also

- [Capabilities XML Elements](capabilities-xml-elements.md)  
- [Basic Authentication](basic-authentication.md) 
- [Forms-Based Authentication](forms-based-authentication.md)
- [Getting Ready to Release an OSC Provider](getting-ready-to-release-an-osc-provider.md)

