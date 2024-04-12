---
title: "Types of Client Applications"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 52ce22a9-3ec2-481c-bb91-7a5bcca817f5
 
 
---

# Types of Client Applications

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are primarily two types of messaging clients: those that handle interpersonal messages (IPM) and those that handle interprocess communication (IPC) messages. Within those types, messaging client applications can be categorized as follows:
  
- Person-to-person
    
- Person-to-machine
    
- Machine-to-person
    
- Machine-to-machine
    
- Mix of persons and machines
    
Person-to-person applications involve a person initiating the exchange of messages and another person responding. This category of applications includes traditional email applications as well as more structured exchanges such as document routing or expense approval.
  
Person-to-machine applications involve a person initiating the exchange of messages and a machine responding. This category includes applications that use email to, for example, submit a database query or subscribe to a mailing list.
  
Machine-to-person applications involve a machine initiating the exchange of messages and a person responding. This category includes applications that distribute documents such as news feeds and opinion surveys.
  
Machine-to-machine applications involve a machine initiating the exchange of messages and a machine responding. This category includes applications such as link heartbeat monitoring and directory and database replication.
  
The final category, a mix of persons and machines, involves a more complex scenario. This category includes applications that do not necessarily transmit messages between senders and recipients. Instead they might post them directly into a public folder or to a web-site forum supported by a message store. The messages can then be consumed on demand by other readers, an administrator, or a software agent.
  
If you are writing a person-to-person application, machine-to-person application, or an application that posts messages to public forums, design your application to send and receive IPM messages. If you are writing a person-to-machine or machine-to-machine application, it can be designed to send and receive IPC messages. Any application that requires the interaction of a human user must support IPM messages. Applications that involve both people and machines in a variety of scenarios often must support both IPM and IPC messages. The only real difference between the two classes is that IPM messages in a message store are visible to users of messaging clients, while IPC messages usually are not visible to the client application users. 
  
Rather than limiting your messages to the capabilities provided by the MAPI superclasses, IPM and IPC, you can customize and enhance these classes by creating new IPM or IPC subclasses. Creating message subclasses involves inventing new message classes that inherit from the superclasses. For example, if your person-to-person application specializes in customer relationship management, you can subclass the IPM superclass by defining an IPM.Contact.Customer class and create properties that describe a customer. In addition to supporting these custom properties, your IPM.Contact.Customer messages will inherit the properties supported by all IPM messages.
  

