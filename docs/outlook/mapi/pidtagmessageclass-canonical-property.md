---
title: "PidTagMessageClass Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMessageClass
api_type:
- HeaderDef
ms.assetid: 1e704023-1992-4b43-857e-0a7da7bc8e87
description: "Last modified: March 09, 2015"
---

# PidTagMessageClass Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a text string that identifies the sender-defined message class, such as IPM.Note. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_CLASS, PR_MESSAGE_CLASS_A, PR_MESSAGE_CLASS_W  <br/> |
|Identifier:  <br/> |0x001A  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Common  <br/> |
   
## Remarks

The message class specifies the type of the message. It determines the set of properties defined for the message, the kind of information the message conveys, and how to handle the message. 
  
These properties contain strings concatenated with periods. Each string represents a level of subclassing. For example, IPM.Note is a subclass of IPM and a superclass of IPM.Note.Private. 
  
These properties must consist of the ASCII characters 32 through 127 and must not end with a period (ASCII 46). Sort and compare operations must treat it as a case-insensitive string. The maximum possible length is 255 characters, but in order to allow MAPI room to append qualifiers it is recommended that the original length be kept under 128 characters. 
  
Every message is required to furnish these properties. Normally, the client application creating a new message sets it as soon as [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) returns successfully. But if the property has not been set when the client calls [IMAPIProp::SaveChanges](imapiprop-savechanges.md), the message store should set it to IPM. 
  
The values defined by MAPI are: 
  
```cpp
IPM.Note for a standard interpersonal message 
REPORT.<subject message class>.DR for a delivery report 
REPORT.<subject message class>.NDR for a nondelivery report 
REPORT.<subject message class>.IPNRN for a read report 
REPORT.<subject message class>.IPNNRN for a nonread report 
 
```

IPM and IPC are intended to be superclasses only, and a message should have at least one subclass qualifier appended before being stored or submitted. For more information on message class usage, see [Message Classes](mapi-message-classes.md). For lists of required and optional properties for message classes, see the subtopics of [About Message Properties](message-properties-overview.md).
  
A custom message class can define properties in a reserved range for use with that message class only. For more information, see [About Property Identifiers](mapi-property-identifier-overview.md). 
  
Message classes control which receive folder an incoming message is stored in. For more information, see the [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) method. 
  
For more information on using message classes with forms and form servers, see [Choosing a Message Class](choosing-a-message-class.md). 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
[[MS-OXOUM]](http://msdn.microsoft.com/library/2a0696c5-2caf-4f20-87fb-085db430afec%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for representing voice mail and fax messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

