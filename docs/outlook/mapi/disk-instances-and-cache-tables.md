---
title: "Disk Instances and Cache Tables"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d556ff4d-e2f3-4c83-a93f-b1bfda5abc8c
description: "Last modified: July 23, 2011"
---

# Disk Instances and Cache Tables

**Applies to**: Outlook 2013 | Outlook 2016 
  
To activate a form, its executable files must be available on the user's computer. If they are not available, they must be copied from the form library to the local disk. To do this, the default form manager creates a subdirectory in the user's Windows directory to contain the form's executable files (.EXEs,.HLPs). This directory is referred to as the disk instance of the form.
  
The default form manager maintains a table of all disk instances so that if a disk instance already exists it can be used without having to copy files from the form library to the user's disk. The table of disk instances is managed as a least-frequently-used cache. If a new disk instance is needed, it is copied to the user's computer, replacing the least-frequently-used disk instance. The disk instance cache table is then updated to reflect the latest configuration. The size of the disk cache is a user-configurable option, enabling users to balance speed with available disk capacity.
  
In addition to the disk instance cache, the default form manager maintains a running instance table that lists all running instances of form servers on the user's computer. This uses MAPI's ability to keep idle form instances running in an invisible state until a form of that form server's message class is activated. In other words, form servers can be cached in RAM to minimize the number of times a form's executable must be located within a form library and loaded into memory from disk or over the network. Like the disk instance cache, the running instance cache behaves in a least-frequently-used fashion so that a running form instance can be purged from the cache to make room for another form instance. This cache is searched for a running instance of a form server before the form libraries are searched for the form server.
  
> [!NOTE]
> The default form manager displays a progress indicator when installing a form on a user's workstation, enabling the user to cancel the operation. This is especially useful if the user's connection to the form server's executable file is over a low bandwidth network. 
  
## See also

- [MAPI Forms](mapi-forms.md)

