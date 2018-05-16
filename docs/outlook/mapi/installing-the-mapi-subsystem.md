---
title: "Installing the MAPI Subsystem"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 29fb4c44-1a59-457e-813b-a982bd72891c
description: "Last modified: March 09, 2015"
 
 
---

# Installing the MAPI Subsystem

  
  
**Applies to**: Outlook 
  
Supported versions of Windows install the MAPI stub library, Mapi32.dll, in the  _\<drive\>_\Windows\System32 folder. 
  
The supported versions of Windows are as follows:
  
- Windows 7.
    
- Windows Vista.
    
- Windows Server 2008.
    
- Windows Server 2003.
    
- Windows XP.
    
To correctly install the MAPI subsystem, install an application that contains a MAPI-based subsystem, such as Microsoft Outlook.
  
You can find information about a computer's MAPI subsystem installation in the system registry. All values in the registry entries are character strings. 
  
Message service installation programs are responsible for creating the installation information in the following system registry key: 
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Messaging Subsystem`
  
Message services must add entries to the system registry. 
  
The following table summarizes how clients retrieve version information for the MAPI subsystem on their computer.
  
|**To check**|**Registry**|
|:-----|:-----|
|Availability of MAPI  <br/> |Look for  `MAPIX=1`.  <br/> |
|Available version of MAPI  <br/> |Look for a MAPIXVER string of the form " _x.x.x_".  <br/> |
   
## See also

#### Concepts

[MAPI Programming Overview](mapi-programming-overview.md)

