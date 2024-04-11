---
title: "Supporting Message Service Installation"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 822e07bc-0bca-4485-8938-2264315161e2
 
 
---

# Supporting Message Service Installation

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The setup program for installing your message service should do the following:
  
1. Copy message service files, such as the message service and service provider DLLs, from a CD or disk, to a local drive on the workstation. The files that need to be copied depend on your message service. Typically you will copy at least one DLL.
    
2. Add entries to the Mapisvc.inf configuration file. For more information about how to modify this file to support the service providers in your message service, see [File Format of MapiSvc.inf](file-format-of-mapisvc-inf.md).
    
3. Add entries, as appropriate, to the system registry for message services. For more information about how the entries should appear in the system registry, see [Installing the MAPI Subsystem](installing-the-mapi-subsystem.md).
    
4. Create a default profile if one does not yet exist by using one of the following items:
    
  - The Profile Wizard to create a profile by using user interaction through a series of dialog boxes. For more information about using the Profile Wizard, see [Creating a Profile by Using the Profile Wizard](creating-a-profile-by-using-the-profile-wizard.md).
    
  - The Control Panel to create a profile by using user interaction. The Control Panel offers the user more flexibility than the Profile Wizard for configuring the message services and setting profile properties. 
    
Place the setup program in a designated public directory. This is important because most configuration clients, such as the Control Panel, require that users enter the name of the directory. The Control Panel invokes a setup program when a user clicks the **Add** button, invokes the **Have Disk** dialog box, and specifies the path to the program. The Control Panel runs the program and calls your message service's entry point function with the  _ulContext_ parameter set to MSG_SERVICE_INSTALL. 
  
> [!CAUTION]
> Because profiles are an expendable part of the MAPI architecture, be sure that your installation program does not store anything in the default profile that would be difficult to recreate. There are no utilities for profile recovery, for moving profiles from one computer to another, for off-line backup, or for individual or global restoration from backup copies. 
  
## See also



[Message Service Implementation](message-service-implementation.md)

