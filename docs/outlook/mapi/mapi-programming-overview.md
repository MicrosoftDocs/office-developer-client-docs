---
title: "MAPI Programming Overview"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 30ac637a-874f-4660-b5d0-d28d69486f64
description: "Last modified: June 25, 2012"
---

# MAPI Programming Overview

 **Last modified:** June 25, 2012 
  
 * **Applies to:** Outlook * 
  
This Microsoft Outlook Messaging API (MAPI) Reference is written for C and C++ developers with a variety of needs and experience with messaging. For those developers who want to use MAPI to augment their applications that have messaging features, no specific prerequisite knowledge is required. You need a background in messaging and the Component Object Model (COM) to use MAPI to create full-scale workgroup applications or drivers for specialized messaging system services.
  
Before starting development work, you should consider the following information about how to use MAPI, the logon process, and how profiles and message services are created and configured.
  
The Messaging Application Program Interface (MAPI) is an extensive set of functions that developers can use to create mail-enabled applications. The full function library is known as MAPI. MAPI enables complete control over the messaging system on the client computer, creation and management of messages, management of the client mailbox, service providers, and so on.
  
> [!NOTE]
> Extended MAPI is the same as MAPI, and is simply referred to as MAPI in the MAPI documentation. 
  
 **Simple MAPI**
  
Simple MAPI provides a set of functions that enables you to add a basic level of messaging functionality to Microsoft Windows-based applications.
  
> [!IMPORTANT]
> The Simple MAPI function MAPISendMail is supported by Microsoft Outlook 2013 and Microsoft Outlook 2010. Other Simple MAPI functions have been deprecated in Windows. 
  

