---
title: "MAPI Feature Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 22cf56c5-2804-40a8-99e6-a6d127897720
description: "Last modified: July 23, 2011"
---

# MAPI Feature Overview
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI has several key features that enable it to provide a consistent way for developers to work with and use different messaging systems in a seamless fashion. These features include a comprehensive and open programming interface, and support for industry standards. 
  
Because MAPI is an open programming interface, it provides services in a generic way, enabling users to add any necessary customization now and in the future. The MAPI programming interface fulfills the requirements of client applications with diverse messaging needs, such as a word processing application that requires only the ability to send documents, or a workgroup application that requires the ability to share and store different types of data. In fact, any application that needs to either exchange or store information in a particular format can benefit from the MAPI programming interface. Any service provider can use the interface to expose the unique features of its messaging system, selecting those features that provide the most benefit to application users.
  
MAPI provides separation between the programming interface used by the front-end messaging client applications and the programming interface used by the back-end service providers. Separating the client interface from the service provider enables a single application to use multiple messaging systems and multiple applications to use a single service provider. Every component works with a common Microsoft Windows-based user interface. This is a great benefit to users. Users can select from a variety of systems, depending on their needs at any one time, and can work consistently with each selected system, thereby providing true independence from specific messaging systems. 
  
For example, a single messaging client application can receive messages from a fax, voice mail, and an RSS feed. Messages from all of these systems can be placed in a single location, or universal Inbox, on arrival. Having a single application handle all of these systems lessens the cost of development, user training, and system administration. 
  
Separating the client interface from the provider interface removes any programming dependencies placed on the application by the messaging system and vice versa. Developers of client applications and service providers write code to a standard set of MAPI features, rather than a diverse set of application-specific or messaging system-specific features. Developers focus only on their component, whether it is a client or service provider, and MAPI handles the rest, reducing development time and costs.
  
The MAPI programming interface provides a comprehensive set of features. MAPI is aimed at the powerful new market of workgroup applications — applications that communicate with such different messaging systems as fax, DEC All-In-1, voice mail, and public communications services such as AT&T Easylink Services, CompuServe, and MCI MAIL. The MAPI interface enables service providers to be made available for all of these systems. 
  
MAPI-compliant objects are similar in form to Component Object Model (COM) objects. COM objects implement a set of methods that belong to one or more interfaces, or collections of related functions that define how objects behave and operate in COM. Users access COM objects only through pointers to these interfaces.
  
MAPI provides cross-platform support through such industry standards as SMTP and X.400. You can run MAPI applications on Windows 7, Windows Vista, Windows Server 2008, Windows Server 2003, and Windows XP. 
  
## See also

- [MAPI Features and Architecture](mapi-features-and-architecture.md)

