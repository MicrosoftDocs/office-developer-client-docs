---
title: "Form Configuration File [Platforms] Section"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 3b9b3dc0-4f82-468b-8e77-0374c5b196f4
description: "Last modified: March 09, 2015"
---

# Form Configuration File [Platforms] Section

**Applies to**: Outlook 2013 | Outlook 2016 
  
The **[Platforms]** section lists the complete set of platforms supported by this form. Each platform entry consists of the prefix **Platform.** _string_, where  _string_ is an arbitrary string code for the platform. Each string corresponds to the **CPU** entry of an individual **[Platforms]** sections. Each entry in a **[Platforms]** section defines a  _platform string_ that references a subsequent **[Platform.** _platform string_ **]** section as shown here. 
  
The **[Platforms]** section lists the complete set of platforms supported by this form. Each platform entry consists of the prefix **Platform.** _string_, where  _string_ is an arbitrary string code for the platform. Each string corresponds to the **CPU** entry of an individual **[Platforms]** sections. Each entry in a **[Platforms]** section defines a  _platform string_ that references a subsequent **[Platform.** _platform string_ **]** section as shown here. 
  
**[Platforms]**
  
**Platform**. _string_ =  _platform string_
  
Following is an example of a **[Platforms]** section. 
  
```cpp
[Platforms]
Platform.1 = NTx86
Platform.2 = Win95

```

Each **[Platform.** _platform string_ **]** section contains the two required entries, **CPU** and **OSVersion**. The **CPU** entry specifies the processor, and the **OSVersion** entry specifies the operating system. Valid **CPU** values are described in the following table. 
  
|**CPU Entry**|**Processor**|
|:-----|:-----|
|Ix86  <br/> |Intel 80x86 and Pentium series processors, as well as equivalent processors from AMD, Cyrix, NextGen and other manufacturers.  <br/> |
|MIPS  <br/> |MIPS R4000 series processors.  <br/> |
|AXP  <br/> |Digital Equipment Corporation Alpha AXP processor.  <br/> |
|PPC  <br/> |Motorola Power PC series processors.  <br/> |
|M68  <br/> |Mororola 68x00 series processors.  <br/> |
   
Valid **OSVersion** values are described in the following table. 
  
|**OSVersion Entry**|**Operating System**|
|:-----|:-----|
|Win3.1  <br/> |Windows 3.1 and Windows for Workgroups 3.11.  <br/> |
|WinNT3.5  <br/> |Windows NT 3.5 or lower.  <br/> |
|Win95  <br/> |Windows 95.  <br/> |
|WinNT4.0  <br/> |Windows NT 4.0.  <br/> |
|Mac7  <br/> |Macintosh System 7.  <br/> |
   
Additionally, the **[Platform.** _platform string_ **]** section must contain either a **File** or **LinkTo** entry. The **File** entry lists the form server application executable file that the form library maintains and loads into a new subdirectory in the disk cache when the form is launched. If a **LinkTo** entry is used instead, it contains the name of a different platform string from which the **File** information is taken. This is useful if one version of a form supports multiple platforms. 
  
The **Registry** entry is used whenever the **File** entry is used, it identifies the registry key for the form library where the executable file for the form server application is stored. Strings preceded by a backslash ( \ ) are placed at the root of the registry. Strings not preceded by a backslash are placed in the HKEY_CLASSES_ROOT\CLSID\  _GUID_\ registry key, where  _GUID_ is the **GUID** of the form. The characters "%d" can be used to indicate the pathname of the directory from which the form configuration file has been read. This is useful for specifying other files with pathnames relative to the form configuration file. **Multiple File** or **Registry** entries can be specified by using File or Registry as a prefix followed by any other text. The format for the **[Platform.** _platform string_ **]** section is: 
  
- **[Platform.** _platform string_ **]**
    
- **CPU** =  _string_
    
- **OSVersion** =  _string_
    
- **File** =  _path_
    
- **LinkTo** =  _string_
    
- **Registry** =  _string_
  
The following are two example **[Platform.** _platform string_ **]** sections, one using the **File** entry and one using the **LinkTo** entry. 
  
```cpp
[Platform.NTx86]
CPU = ix86
OSVersion = WinNT3.5
File = \helpdesk.exe
Registry = Local Server = %d\helpdesk.exe
[Platform.Win95]
CPU = ix86
OSVersion = Win95
LinkTo = NTx86

```

The **[Platform.** _platform string_ **]** section is ignored when adding a form to the local form library, when it is assumed that the installer has placed the files constituting the message class handler into available local storage as named in the handler's section in the OLE registry, and has done the OLE registration in the system's registry. 
  

