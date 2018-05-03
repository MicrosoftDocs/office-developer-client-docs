---
title: "About the last update time of an Offline Address Book"
 
 
manager: soliver
ms.date: 12/8/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: d8c554c5-89ac-9b32-5561-8d8178d2525a
description: "An Offline Address Book (OAB) provides Outlook users in a disconnected state access to directory information from the Global Address List (GAL) and from other address books. It is a copy of an Address Book that Outlook has downloaded from an Exchange server to provide offline access."
---

# About the last update time of an Offline Address Book

An Offline Address Book (OAB) provides Outlook users in a disconnected state access to directory information from the Global Address List (GAL) and from other address books. It is a copy of an Address Book that Outlook has downloaded from an Exchange server to provide offline access.
  
Exchange administrators can choose which Address Books to make available for users who work offline. To create a copy of an Address Book, Exchange generates new OAB files, compresses the files, and places them on a local share. Depending on how Outlook is configured, Outlook downloads the OAB files either from the Web or from a Public Folder to a client computer for use in a disconnected state. Outlook periodically checks for and downloads OAB updates.
  
Outlook solutions that want to provide their users offline access to an OAB may need to find out when the OAB was last updated from the Exchange server. To find the last update time of an OAB, solutions can use the following entry in the Windows registry: **HKCU\Software\Microsoft\Exchange\Exchange Provider\OAB Last Modified Time**. The type of this registry entry is **REG_BINARY**. The data is 8 bytes in size. You can convert the data to a 64-bit [FILETIME](http://msdn.microsoft.com/library/9baf8a0e-59e3-4fbd-9616-2ec9161520d1%28Office.15%29.aspx) structure specifying a Universal Coordinated Time (UTC) value that Outlook last downloaded the OAB files from the Exchange server to the client computer. 
  
## See also

#### Other resources

[Managing Offline Address Books](http://msdn.microsoft.com/library/b7f26eca-b93b-4834-ba50-11febdefbb18.aspx)

