---
title: "MAPI Profile Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d6c57be6-2397-4ab1-a912-028454dffc44
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Profile Overview

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A profile is a collection of information about the message services and service providers that a user of a client application wants to be available during a particular MAPI session. Every user has at least one profile; many users keep several. For example, a user might have one profile to work with a server-based message store service and another profile to work with a message store service on the local computer. A user might want to access one set of messaging systems by using the appropriate transport services for part of the day and another set for the rest of the day. Profiles provide a flexible way to select combinations of messaging system services. 
  
Profiles can have names up to 64 alphanumeric characters in length. The names can include accent characters, the underscore, and embedded spaces, and cannot include leading or trailing spaces. 
  
Profiles are organized hierarchically and divided into sections, with one section for each message service and one section for each service provider in a service. The related sections are linked, making it easier to navigate through the information. Each section contains a series of entries that MAPI or a client application uses for configuration.
  
The entries included in a profile vary from message service to message service. Some of the common entries include the following:
  
- The name of each message service or service provider.
    
- The name of the DLLs that contain service providers and message services.
    
- The name of each message service's entry point function.
    
- A list of the service providers that make up each message service.
    
Profiles can be created at installation time, when MAPI or a message service is loaded onto a computer, or at any later time. MAPI provides the Profile Wizard for profile administration. 
  
The Profile Wizard is an application that creates new profiles with a minimum amount of work. The wizard uses default values for settings wherever possible, saving users time and effort. Users enter values only when absolutely necessary. For more information, see [Creating a Profile by Using the Profile Wizard](creating-a-profile-by-using-the-profile-wizard.md). You can also use the Office Customization Tool to create a new profile. For more information, see [Office Customization Tool](https://go.microsoft.com/fwlink/?LinkId=123000).
  
## See also



[MAPI Features and Architecture](mapi-features-and-architecture.md)

