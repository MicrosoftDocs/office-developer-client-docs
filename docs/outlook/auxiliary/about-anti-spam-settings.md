---
title: "About anti-spam settings" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 04e00e49-c12d-4517-8574-410741d0fa06
description: "Outlook allows users to specify settings for each account to help protect the account from spam. Such anti-spam settings are stored in a section designated for that account in the user's profile."
---

# About anti-spam settings

Outlook allows users to specify settings for each account to help protect the account from spam. Such anti-spam settings are stored in a section designated for that account in the user's profile. Use the [PROP_ACCT_PREFERENCES_UID](prop_acct_preferences_uid.md) property to obtain the unique ID (UID) for the section in the profile that stores the user's preferences for this account, including the anti-spam settings. 
  
Use the following properties to obtain anti-spam settings for the account:
  
- [PidTagSpamJunkSenders](https://msdn.microsoft.com/library/3c5182a7-7d7a-48e8-b9cb-5abd7739f0fd%28Office.15%29.aspx)—Specifies a semicolon-delimited list of email addresses and domains that the user has specified as blocked senders for the account.
    
- [PidTagSpamThreshold](https://msdn.microsoft.com/library/2b2d6b8e-e3dd-4a9b-8bb5-53add675605d%28Office.15%29.aspx)—Specifies the level of spam-filtering that the user has specified for the account. The following table shows the supported values.
    
|Supported value |Definition |
|:-----|:-----|
|None  <br/> |0xFFFFFFFF  <br/> |
|Low  <br/> |0x00000006  <br/> |
|Medium  <br/> |0x00000005  <br/> |
|High  <br/> |0x00000003  <br/> |
   
- [PidTagSpamTrustedRecipients](https://msdn.microsoft.com/library/59f43316-3ff6-4ed0-bc29-b31039192b08%28Office.15%29.aspx)—Specifies a semicolon-delimited list of email addresses and domains that the user has specified as trusted recipients for the account.
    
- [PidTagSpamTrustedSenders](https://msdn.microsoft.com/library/8e3f0094-e64b-4828-ba8f-5eed35f85366%28Office.15%29.aspx)—Specifies a semicolon-delimited list of email addresses and domains that the user has specified as trusted senders for the account.
    
## See also

- [About the Account Management API](about-the-account-management-api.md)
- [Add names to the Junk Email Filter lists](https://office.microsoft.com/en-us/outlook-help/add-names-to-the-junk-email-filter-lists-HA010355043.aspx?CTT=1)

