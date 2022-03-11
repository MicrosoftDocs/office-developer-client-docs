---
title: "attFrom"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 2d405268-bb33-4863-be38-2d17e8fc956e
---

# attFrom

**Applies to**: Outlook 2013 | Outlook 2016
  
The **attFrom** attribute is encoded as a **TRP** structure which encodes the display name and email address of the sender, followed by the display name and address of the sender, followed by any necessary padding. The format for **attFrom** is as follows:
  
**attFrom**: _TRP-structure_ sender-display-name  _sender-address_ padding

The sender-display-name is a null-terminated string that is padded with an additional null character, if necessary, to reach a 2-byte boundary. The padding at the end of the **attFrom** encoding consists of as many null characters as needed to reach a **sizeof(TRP)** boundary.
  
_TRP-structure:_ **trpidOneOff** cbgrtrp cch cb

For the **attFrom** item, the **TRP**-structure is always a one-off encoding, so the trpid off the **TRP**-structure field is always **trpidOneOff**. The cbgrtrp, cch, and cb items correspond to the remaining fields of the **TRP** structure.
  
The cbgrtrp field is calculated as the sum of **(sizeof(TRP) \ * 2)**, the length of the null-terminated sender-display-name with its padding, and the length of the null-terminated sender-address.
  
The cch field is calculated as the length of the null-terminated display-name with its padding.
  
The cb field is calculated as the length of the null-terminated sender-address.
  
_sender-address:_ address-type **:** address **'\0'**

The sender-address is a string that is composed of four parts, the address-type, a literal colon (:), the address itself, and a terminating null character. For example, the string `fax:1-909-555-1234\0` would be a legal sender-address value.
  