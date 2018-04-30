---
title: "MAPI Message Classes"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 64ef2bbb-585c-4908-8ad4-a1c954057e9b
description: "Last modified: July 23, 2011"
---

# MAPI Message Classes

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Every message has a message class property, **PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)), which identifies the type, purpose, or content of the message. **PR_MESSAGE_CLASS** is a required property on all new messages. A message's class determines the form that is used to present the message to the user and the folder for placing incoming messages. 
  
Message classes are case-sensitive character strings that contain ASCII characters 32 through 127 and are delimited by periods, but they cannot end with a period. Each string represents a level of subclassing, and there is no limit to the number of levels allowed. 
  
For example, most messages that client applications send and receive fall into the **IPM** message class, a broad category that describes all interpersonal messages (that is, messages that are meant to be read by a human user, rather than programmatically by a computer). Message store providers more precisely describe an IPM message by creating an **IPM** subclass. The **IPM** subclass inherits the properties of the **IPM** message class. Subclasses of the **IPM** class are named by concatenating other character strings onto the IPM identifier, such as **IPM.Note** to describe a note message and **IPM.Contact** to describe a contact message. 
  
To handle the display and management of IPM messages, clients can use a standard form that MAPI provides. To handle the display and management of new message classes, you as a client application developer have two options:
  
1. You can create a new form by using the set of MAPI-defined form interfaces that a standard client can use.
    
2. You can write your own client by implementing a complete, standalone application. 
    
Although clients should set the **PR_MESSAGE_CLASS** property for every outgoing message to a subclass of either **IPM** or **IPC**, the message store provider has the ultimate responsibility for setting it. Therefore, if a client sends a message without setting its message class, the message store provider sets it to the appropriate default value for the appropriate type of client. The default message class for interpersonal messaging clients is **IPM**; the default message class for interprocess communication clients is **IPC**. 
  
Message classes have a length restriction of 255 characters. However, message classes should not exceed 127 characters to support the message classes used in reports. Report message classes are based on the class of the original message, with two additions: a prefix and a suffix. The prefix REPORT indicates that the message is a report, and the suffix indicates the type of report: DR (delivery report), NDR (nondelivery report), IPNRN (read report), or IPNNRN (nonread report). Note that these length restrictions are given in characters; on platforms that use a double-byte character set, the actual byte count might be higher. 
  
Message store providers should return MAPI_E_INVALID_PARAMETER from their [IMAPIProp::SetProps](imapiprop-setprops.md) method implementations when a client attempts to assign a string that exceeds the allowable limit for their message class. 
  
## See also

#### Concepts

[MAPI Messages](mapi-messages.md)

