---
title: "PROP_ACCT_PREFERENCES_UID"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: ec0aac33-624e-48f7-8177-8f7b8db6af7d
description: "Retrieves the unique identifier (UID) for the profile section that stores the account preferences."
---

# PROP_ACCT_PREFERENCES_UID

Retrieves the unique identifier (UID) for the profile section that stores the account preferences. 
  
## Quick info

See [IOlkAccount](iolkaccount.md).
  
|||
|:-----|:-----|
|Identifier:  <br/> |0x0022  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Property tag:  <br/> |0x00220102  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

Use **PROP_ACCT_PREFERENCES_UID** in calls to [IMAPISupport::OpenProfileSection](http://msdn.microsoft.com/library/cd1fa994-9531-46c4-94e5-505e7f90b884%28Office.15%29.aspx) to retrieve the profile section that contains account preferences. 
  
## See also

- [About the Account Management API](about-the-account-management-api.md)
- [About anti-spam settings](about-anti-spam-settings.md)

