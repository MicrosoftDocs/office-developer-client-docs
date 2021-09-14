---
title: "One-off addresses"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 9224c694-b26f-42c7-9404-ee2dd832cfbb
description: "Last modified: March 09, 2015"
---

# One-off addresses

**Applies to**: Outlook 2013 | Outlook 2016 
  
One-off addresses are used to send messages to one-off recipients, recipients that do not have a corresponding entry in any of the session's address book containers. Clients can create one-off addresses when they add new entries to the address book or new recipients to the recipient list of an outgoing message. One-off addresses can be added to any container that is modifiable.
  
To create a one-off address, clients use a special template containing edit controls for entering all of the information that makes up a one-off address. One-off addresses, like addresses of other types, use a predefined format. The one-off address format is defined by MAPI as follows:
  
`Display name[Address type:Email address]`
  
There are six components to this format and some rules about quoting characters. The components are described in the following table.
  
|**Component**|**Usage**|**Description**|
|:-----|:-----|:-----|
|Display name  <br/> |Optional  <br/> |If not present, **IAddrBook::ResolveName** uses the visible part of the email address as the display name. May include blanks. For more information, see [IAddrBook::ResolveName](iaddrbook-resolvename.md).  <br/> |
|[  <br/> |Required  <br/> |Delineates the start of the type and address information.  <br/> |
|]  <br/> |Required  <br/> |Delineates the end of the type and address information. If anything other than white space follows this character, the entry is not treated as a custom recipient.  <br/> |
|Address type  <br/> |Required  <br/> |Type of address; maps to a specific address format. For more information, see [MAPI Address Types](mapi-address-types.md).  <br/> |
|:  <br/> |Required  <br/> |Separates the address type from the email address.  <br/> |
|Email address  <br/> |Required  <br/> |Address of the recipient. May include blanks.  <br/> |
   
MAPI uses particular sets of quoting characters to allow addresses to contain special characters such as comma (,), left bracket ([), and colon (:) and some untypeable characters such as the carriage return or line feed or any other hexadecimal equivalent. The quoting character is the backslash (\). Therefore, if clients or providers must insert a backslash in an address, they must preceed it with the quoting character ("\\").
  
Clients and service providers can use this quoting technique in any of the nonfixed, typeable fields. For example, the following entry translates to Bill Lee as the display name, MSPEER as the address type, and \\billll\in as the email address:
  
`Bill Lee[MSPEER:\\\\billl\in]`

To insert special nontypeable characters, clients and service providers use a quoting character followed by an x and two hexadecimal digits to represent their hexadecimal equivalent. For example, if an address has a nontypeable character that equates to a carriage return, (\0d) in hexadecimal, a client would enter them as:
  
`Fax Recipient[fax:recipient\x0dbuilding\x0doffice\x0d555-1212\x0d]`

**IAddrBook::ResolveName** also automatically parses most SMTP addresses, looking for addresses with the following format: 
  
`XXX@YYY.ZZZ`

Although not all of the possible RFC822 formats are handled, this automatic parsing is adequate for most users. **ResolveName** includes this functionality to enable users to enter SMTP addresses directly into a message and have that message go to the Internet user. The XXX, YYY, and ZZZ components of the address can be one or more characters. The at sign (@) cannot be included in either the XXX, YYY, or ZZZ address components and the YYY component also cannot include the period. Because the following characters are special characters in SMTP addresses, MAPI automatically converts a display name containing these characters into a one-off address: 
  
- \>\>
    
- @
    
- \<\>
    
- .
    
Every one-off address is assigned a corresponding one-off entry identifier. To make this assignment, clients call **IAddrBook::CreateOneOff** and transport providers call **IMAPISupport::CreateOneOff**. For more information, see [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) and [IMAPISupport::CreateOneOff](imapisupport-createoneoff.md). When processing incoming messages, transport providers create one-off entry identifiers for gateway addresses and for addresses that cannot be handled by the transport's associated address book providers. Transport providers check the type of each address in a message to determine if it can be handled by an address book provider associated with the transport. If it cannot, transport providers call **IMAPISupport::CreateOneOff** to associate the address with a one-off entry identifier. 
  
One-off entry identifiers include the following information in the following order:
  
1. **MAPIUID**
    
2. Version
    
3. Flags
    
4. Display name
    
5. Address type
    
6. Email address
    
In the calls to **IAddrBook::CreateOneOff** and **IMAPISupport::CreateOneOff**, clients and transport providers can set a flag that indicates whether or not the recipient represented by the one-off address can process formatted text or embedded OLE objects. To indicate that a recipient can handle formatted text and OLE objects, clients and transport providers set the MAPI_SEND_NO_RICH_INFO flag in the  _ulFlags_ parameter. MAPI then sets the one-off recipient's **PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) property to FALSE. When this flag is not set, MAPI sets **PR_SEND_RICH_INFO** to TRUE unless the one-off address is interpreted as an SMTP address. In this one case, **PR_SEND_RICH_INFO** defaults to FALSE. 
  
## See also

- [IAddrBook::ResolveName](iaddrbook-resolvename.md)

