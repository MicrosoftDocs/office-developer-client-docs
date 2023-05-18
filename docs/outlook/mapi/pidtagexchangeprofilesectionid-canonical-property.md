---
title: "PidTagExchangeProfileSectionId Canonical Property"
description: Outlines the PidTagExchangeProfileSectionId canonical property, which contains a dynamically generated GUID.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagExchangeProfileSectionId
api_type:
- HeaderDef
ms.assetid: 4ad2f417-be8f-4fc8-9321-82097289074b
---

# PidTagExchangeProfileSectionId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a dynamically generated GUID used to determine an account when you are using multiple Microsoft Exchange Server accounts.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_EMSMDB_SECTION_UID  <br/> |
|Identifier:  <br/> |0x3d150102  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Multiple Exchange Accounts  <br/> |
   
## Remarks

Microsoft Outlook 2010 and Microsoft Outlook 2013 support multiple Exchange accounts instead of one single Exchange account. To accommodate multiple Exchange accounts, the MAPI profile layout was changed. In Microsoft Office Outlook 2007 and earlier, profiles contained a fixed profile section dedicated to Exchange settings such as server name, user name, and Offline Folder file (.ost). location. These settings were identified by using a unique identifier, the **pbGlobalProfileSectionGuid** property. The section used for Exchange settings is called the Exchange Global Profile Section. 
  
A fixed profile section location is no longer sufficient to accommodate multiple Exchange accounts. Instead, for each Exchange account in your profile, a section exists that is dedicated to settings for that account. The new section used for Exchange settings is identified by the unique identifier **emsmdbUID**.
  
In the message service profile section for the Exchange account, you can find a property that contains a GUID that is dynamically generated at the time that the account is created. This GUID is stored in the **PidTagExchangeProfileSectionId** property. Message stores and address book containers expose a property to determine which Exchange account they belong to. Accessible in the message services table, each Exchange service exposes this property. 
  
You can retrieve this property through a call to [IMAPIProp::GetProps](imapiprop-getprops.md) on **PidTagExchangeProfileSectionId** after querying for any of the following interfaces: 
  
- [IMsgStore : IMAPIProp](imsgstoreimapiprop.md)
    
- [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
    
- [IABContainer : IMAPIContainer](iabcontainerimapicontainer.md)
    
If the object is not affiliated with Exchange, the call returns **MAPI_E_NOT_FOUND**.
  
You can restrict containers on a **PidTagExchangeProfileSectionId** when displaying the address book. Once you have an opened container, you can query the **emsmdbUID** from it. It is also worth noting that if a recipient was selected from an Exchange address book, the recipient also has the **PidTagExchangeProfileSectionId** in its list of properties. 
  
> [!NOTE]
> Throughout the code samples and function headers, this GUID is known as **emsmdbUID**. 
  
One of the Exchange accounts is marked as the legacy Exchange account. Usually, it is the first account added to the profile. Every call to open **pbGlobalProfileSectionGuid** is redirected to the Exchange global section of the legacy account. The object model calls that interact with the non-legacy Exchange account also interact with the legacy Exchange account. 
  
The legacy Exchange service has the property **PR_EMSMDB_LEGACY** (0x3D18000B), which is set to **true** in the message services table. 
  
The legacy **emsmdbUID** is also stamped in the Outlook Global Profile Section of the profile as **PidTagExchangeProfileSectionId**. Code written to support multiple Exchange accounts should not have to retrieve the legacy **emsmdbUID** because it should get the correct **emsmdbUID**, depending on the account your code is interacting with.
  
## See also



[Using Multiple Exchange Accounts](using-multiple-exchange-accounts.md)


[How To Open the Global Profile Section](/training/paths/configure-user-device-profiles/)
