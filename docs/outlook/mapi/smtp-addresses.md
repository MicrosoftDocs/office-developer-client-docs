---
title: "SMTP Addresses"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 42015740-a94f-4628-bf32-b7fc2fdb9ff6
description: "Last modified: March 09, 2015"
 
 
---

# SMTP Addresses

  
  
**Applies to**: Outlook 
  
The format of SMTP e-mail addresses is defined in RFC 822. MAPI components should handle any address that complies with that standard. However, there is a particular form of RFC 822 address that best encodes MAPI addresses:
  
 _display-name_ **\<** _email-address_ **\>**
  
The angle brackets are included as literals. Blanks are common in display names; they need not be quoted. A typical address might look like this one, which belongs to one of the coauthors of RFC 1521:
  
Nathaniel Borenstein \<nsb@bellcore.com\>
  
If the display name contains characters that have special meaning in SMTP addresses, such as \< or @, the entire display name should be enclosed in double quotes. On outbound mail, if the total length of the e-mail address plus display name exceeds 255 characters, the display name should be dropped.
  
The parts of an SMTP address map into MAPI properties as follows:
  
|**SMTP address component**|**MAPI property**|
|:-----|:-----|
| _display-name_ for all recipients  <br/> |**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |
| _display-name_ for From field  <br/> |**PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))  <br/> |
| _display-name_ for Sender field  <br/> |**PR_SENT_REPRESENTING_NAME** ([PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md))  <br/> |
| _email-address_ <br/> |**PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))  <br/> |
|implicit, always "SMTP"  <br/> |**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |
   
If there is no display name for an address on inbound mail, the entire e-mail address should be used instead. The address type is always SMTP.
  
Recipient properties are taken from the MAPI message's recipient table; sender properties are taken from the message itself.
  

