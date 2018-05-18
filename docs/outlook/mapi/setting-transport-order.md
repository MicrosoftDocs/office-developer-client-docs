---
title: "Setting Transport Order"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4a140ec3-9520-4119-a975-0fb6c1049967
description: "Last modified: July 23, 2011"
 
 
---

# Setting Transport Order

  
  
**Applies to**: Outlook 
  
The MAPI spooler assigns responsibility for outgoing messages based on the address types and identifiers that transport providers declare they can handle. Transport providers publish a list of supported address types and identifiers — stored in **MAPIUID** structures — when MAPI calls their [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method, directly after logon. A recipient's address type is stored in its **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) property.
  
Registering for an address type indicates to MAPI that the transport provider can deliver to recipients with their **PR_ADDRTYPE** property set to the registered address type. Similarly, registering for a **MAPIUID** indicates that the transport provider can deliver to recipients that are represented by entry identifiers with the registered **MAPIUID**.
  
Most transport providers register for one or more address types; few register by **MAPIUID**. Transport providers that are tightly coupled with an address book provider and understand its entry identifier format can register to handle messages by **MAPIUID**, thereby improving performance. These tightly coupled transport providers can extract the recipient's e-mail address and other necessary information from the entry identifier without having to open it with an **IMAPISupport::OpenEntry** call. 
  
MAPI maintains an order for transport providers, used when multiple transport providers have registered for the same address type or **MAPIUID**. You can override this order by calling [IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md) and passing an ordered list of the **MAPIUID**s of all of the active transport providers pointed to by the  _lpUIDList_ parameter.: 
  
To retrieve a list of all of the address types that can be handled by one of the active transport providers, call [IMAPISession::EnumAdrTypes](imapisession-enumadrtypes.md). **EnumAdrTypes** returns an array of strings that describes address types supported by the transport providers that are active in the current session. 
  

