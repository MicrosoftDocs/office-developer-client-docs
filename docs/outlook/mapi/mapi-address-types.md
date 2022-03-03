---
title: "MAPI Address Types"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: eee97982-29be-4dcf-ae11-8a38f0080ea7
 
 
---

# MAPI Address Types

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Every messaging user is associated with an address type, a character string describing the format of the user's address that is stored in the **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) property. Address types map to address formats. That is, by looking at a recipient's address type, client applications can determine how to format an address appropriate for the recipient. 
  
For example, the  `SMTP` address type specifies the standard Internet address: 
  
 `username@companyname.com.`
  
And, the  `EX` address type specifies an Exchange Server address. 
  
All address book entries must have a valid address type. Clients require their users to specify an address type when creating a type of custom recipient unsupported by the address book provider. For the entries that they support, address book providers are required to supply valid address types. 
  
MAPI defines only one address type: MAPIPDL, which stands for personal distribution list.
  
To get a list of the address types supported by all of the transport providers in the session, client applications call the **IMAPISession::EnumAdrTypes** method. For more information, see [IMAPISession::EnumAdrTypes](imapisession-enumadrtypes.md).
  

