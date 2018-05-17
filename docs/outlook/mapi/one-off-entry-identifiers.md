---
title: "One-Off Entry Identifiers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 741d21ae-f14a-4b7f-80aa-91d0f0ff3f34
description: "Last modified: July 23, 2011"
 
 
---

# One-Off Entry Identifiers

  
  
**Applies to**: Outlook 
  
One-off entry identifiers are created by MAPI in the **IAddrBook::CreateOneOff** method and by components that do not have access to the MAPI subsystem, such as gateway components. For more information, see [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md). The following illustration shows the format of a one-off entry identifier.
  
 **One-off entry identifier format**
  
![One-off entry identifier format](media/amapi_69.gif)
  
The first field is a special [MAPIUID](mapiuid.md) structure that identifies the entry identifier as representing a custom recipient. This **MAPIUID** structure must be set to the constant MAPI_ONE_OFF_UID. MAPI_ONE_OFF_UID is defined in the header file MAPIDEFS.H. 
  
The version and flags fields are 16-bit words in Intel byte order. The version field must be set to zero. The flags field can be set to the following values:
  
MAPI_ONE_OFF_NO_RICH_INFO
  
MAPI_ONE_OFF_UNICODE
  
The MAPI_ONE_OFF_NO_RICH_INFO flag is set if a recipient should not receive message content in the Transport Neutral Encapsulation Format (TNEF). This flag is set when MAPI_SEND_NO_RICH_INFO is passed to [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) method. 
  
The MAPI_ONE_OFF_UNICODE flag is set if the display name and e-mail address are Unicode strings. This flag is set when the MAPI_UNICODE is passed to **IAddrBook::CreateOneOff**. When the MAPI_UNICODE flag is not passed to **CreateOneOff**, MAPI assumes that the display name and e-mail address strings are in the workstation's current ANSI character set. ANSI strings generally do not work well in messages that are sent between platforms using different character sets because the code page is not encoded in the entry identifier. To protect against this potential incompatibility, many address types are limited to only those characters that are common across multiple character sets. However, to ensure character set and platform compatibility, clients should use Unicode for the character strings in their messages.
  
The display name is a null-terminated string that corresponds to the recipient's **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property and to the  _lpszName_ parameter passed to **IAddrBook::CreateOneOff**. The character set is Unicode if the MAPI_ONE_OFF_UNICODE flag is set and ANSI if it is clear. 
  
The address type is a null-terminated string that corresponds to the recipient's **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md)) property and to the  _lpszAdrType_ parameter passed to **IAddrBook::CreateOneOff**. 
  
The e-mail address is a null-terminated string that corresponds to the recipient's **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md)) property and to the  _lpszAddress_ parameter passed to **IAddrBook::CreateOneOff**. 
  
> [!NOTE]
> There is no padding in one-off entry identifier structures; the bytes are packed exactly as indicated above and the entry identifier length should not include any bytes beyond the terminating null character of the e-mail address. 
  
Clients and address book providers that manually construct one-off entry identifiers might also need to generate values for the **PR_RECORD_KEY** ( [PidTagRecordKey](pidtagrecordkey-canonical-property.md)) and **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) properties. The record key is identical to the entry identifier. The search key should be formed by concatenating the following fields in the following order:
  
1. The address type, converted to uppercase characters.
    
2. A colon (:).
    
3. The e-mail address, converted to uppercase characters.
    
4. A terminating null character.
    
No character set conversion must be done when generating the search key.
  

