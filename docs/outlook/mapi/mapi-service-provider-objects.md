---
title: "MAPI Service Provider Objects"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f8ade454-2450-49e6-a76f-93801055a7e5
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Service Provider Objects

  
  
**Applies to**: Outlook 
  
Service providers implement many objects. Some are used primarily by MAPI and some are used by client applications. A few objects are implemented by all types of service providers; the rest are specific to a single provider type. The following table describes all of the service provider objects.
  
|**Service provider object**|**Description**|
|:-----|:-----|
|Address book container  <br/> |Contains recipient information for one address book provider in the active profile; address book providers can have one or more address book containers.  <br/> |
|Attachment  <br/> |Contains additional data, such as a file or OLE object, to be associated with a message.  <br/> |
|Control  <br/> |Enables or disables a button and initiates processing when the button is clicked.  <br/> |
|Distribution list  <br/> |Describes a grouping of individual message recipients.  <br/> |
|Folder  <br/> |Contains messages and other message containers.  <br/> |
|Logon  <br/> |Handles service provider event notification and client requests.  <br/> |
|Messaging user  <br/> |Describes an individual recipient of a message.  <br/> |
|Message  <br/> |Contains information that can be sent to one or more recipients.  <br/> |
|Message store  <br/> |Acts as a hierarchically organized database of messages.  <br/> |
|Provider  <br/> |Handles service provider startup and shutdown.  <br/> |
|Spooler hook  <br/> |Performs special processing on inbound and outbound messages.  <br/> |
|Status  <br/> |Provides access to the service provider's state.  <br/> |
|Table  <br/> |Provides access to a summary view of object data in row and column format, similar to a database table.  <br/> |
   
All service providers implement a provider object and a logon object. Provider objects are strictly for bookkeeping; they are used by MAPI to control the startup and shutdown processes. Logon objects service some client requests indirectly. For example, the message store provider's logon object handles notification registration and requests to open message store objects. 
  
Provider and logon objects implement a different interface depending on the type of service provider that supplies the implementation. A message store provider implements the [IMSProvider : IUnknown](imsprovideriunknown.md) and [IMSLogon : IUnknown](imslogoniunknown.md) interfaces in its provider and logon objects, an address book provider implements the [IABProvider : IUnknown](iabprovideriunknown.md) and [IABLogon : IUnknown](iablogoniunknown.md) interfaces, and a transport provider implements the [IXPProvider : IUnknown](ixpprovideriunknown.md) and [IXPLogon : IUnknown](ixplogoniunknown.md) interfaces. 
  
Message hook providers implement spooler hook objects, or objects that filter inbound and outbound messages.
  
Service providers typically use only a few objects. Most frequently, they use a support object that MAPI provides to help implement client requests. The support object is customized for the type of provider that is using it. For all service providers, the support object includes methods for handling event notification, displaying configuration properties, opening objects, and error handling. The rest of the methods are specific to its use; there are customized versions for address book, message store, and transport providers, and for configuration support. For example, the address book support object displays details and custom recipient dialog boxes. The message store support object supports copy and move operations for folders and messages. The transport provider support object includes methods for facilitating interaction with the MAPI spooler. 
  
Some service providers use table data and property data objects — utility objects that MAPI implements. Table data objects enable service providers to manage the underlying data of a table. Property data objects enable service providers to set object and property access. 
  
Transport providers that support the Transport Neutral Encapsulation Format (TNEF) for transferring properties use a TNEF object that MAPI implements to support the [ITnef : IUnknown](itnefiunknown.md) interface. For more information, see [Developing a TNEF-Enabled Transport Provider](developing-a-tnef-enabled-transport-provider.md). 
  
## See also

#### Reference

[ITnef : IUnknown](itnefiunknown.md)
  
[IMSProvider : IUnknown](imsprovideriunknown.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)
  
[IABProvider : IUnknown](iabprovideriunknown.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)
  
[IXPProvider : IUnknown](ixpprovideriunknown.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)
#### Concepts

[Developing a TNEF-Enabled Transport Provider](developing-a-tnef-enabled-transport-provider.md)

