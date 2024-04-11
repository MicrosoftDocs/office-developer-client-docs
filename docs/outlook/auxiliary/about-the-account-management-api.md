---
title: "About the Account Management API"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: eb6b921d-ecf8-3ce5-87ba-ac1632416b05
description: "The Account Management API provides access to account information and supports notifications of account changes. As clients of this API, mail providers do the following:"
---

# About the Account Management API

The Account Management API provides access to account information and supports notifications of account changes. As clients of this API, mail providers do the following:
  
1. Use [IOlkAccountManager](iolkaccountmanager.md) to manage access to accounts and set up notifications about account changes. 
    
2. Implement and use [IOlkAccountNotify](iolkaccountnotify.md) to send notifications about account changes. 
    
3. Use [IOlkEnum](iolkenum.md) to enumerate accounts. 
    
4. Use [IOlkAccount](iolkaccount.md) to get and set properties and other information about an account. Clients obtain this interface through [IOlkAccountManager::FindAccount](iolkaccountmanager-findaccount.md) or [IOlkEnum::GetNext](iolkenum-getnext.md) to access an individual account. 
    
5. Implement and use [IOlkAccountHelper](iolkaccounthelper.md) to provide the account manager helper functionality, including getting an account's profile name and the current MAPI session. 
    
6. Implement and use [IOlkErrorUnknown](iolkerrorunknown.md) to provide extra information about an error in **IOlkAccountManager**, **IOlkAccountNotify**, and **IOlkAccount**. 

##  Account Management API components

The Account Management API provides the following definitions, data types, interfaces, named properties, and properties.
  
### Definitions
  
- [Constants (Account management API)](constants-account-management-api.md)
    
### Data types
  
- [ACCT_BIN](acct_bin.md)
    
- [ACCT_VARIANT](acct_variant.md)
    
### Interfaces
  
- [IOlkAccount](iolkaccount.md)
    
- [IOlkAccountHelper](iolkaccounthelper.md)
    
- [IOlkAccountManager](iolkaccountmanager.md)
    
- [IOlkAccountNotify](iolkaccountnotify.md)
    
- [IOlkEnum](iolkenum.md)
    
- [IOlkErrorUnknown](iolkerrorunknown.md)
    
### Named properties
  
- [PidLidInternetAccountName](pidlidinternetaccountname.md)
    
- [PidLidInternetAccountStamp](pidlidinternetaccountstamp.md)
    
### Properties
  
- [PidTagNextSendAcct](pidtagnextsendacct.md)
    
- [PidTagPrimarySendAccount](pidtagprimarysendaccount.md)
    
- [PROP_ACCT_DELIVERY_FOLDER](prop_acct_delivery_folder.md)
    
- [PROP_ACCT_DELIVERY_STORE](prop_acct_delivery_store.md)
    
- [PROP_ACCT_ID](prop_acct_id.md)
    
- [PROP_ACCT_IS_EXCH](prop_acct_is_exch.md)
    
- [PROP_ACCT_NAME](prop_acct_name.md)
    
- [PROP_ACCT_PREFERENCES_UID](prop_acct_preferences_uid.md)
    
- [PROP_ACCT_SEND_STAMP](prop_acct_send_stamp.md)
    
- [PROP_ACCT_SENTITEMS_EID](prop_acct_sentitems_eid.md)
    
- [PROP_ACCT_STAMP](prop_acct_stamp.md)
    
- [PROP_ACCT_USER_EMAIL_ADDR](prop_acct_user_email_addr.md)
    
- [PROP_ACCT_USER_DISPLAY_NAME](prop_acct_user_display_name.md)
    
- [PROP_MAPI_EMSMDB_UID](prop_mapi_emsmdb_uid.md)
    
- [PROP_MAPI_IDENTITY_ENTRYID](prop_mapi_identity_entryid.md)
    
- [PROP_MAPI_TRANSPORT_FLAGS](prop_mapi_transport_flags.md)
    

