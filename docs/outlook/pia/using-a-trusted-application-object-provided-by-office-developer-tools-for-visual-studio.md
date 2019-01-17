---
title: Using a trusted Application object provided by Office Developer Tools for Visual Studio
TOCTitle: Using a trusted application object provided by Office Developer Tools for Visual Studio
ms:assetid: 3778122f-f60e-48e7-8e72-f3aef168bae2
ms:mtpsurl: https://msdn.microsoft.com/library/Bb622502(v=office.15)
ms:contentKeyID: 55119787
ms.date: 07/24/2014
mtps_version: v=office.15
localization_priority: Normal
---

# Using a trusted Application object provided by Office Developer Tools for Visual Studio

If you are developing a managed add-in by using Office Developer Tools for Visual Studio, always use the [Application](https://msdn.microsoft.com/library/bb646615\(v=office.15\)) object that is provided by Visual Studio. 

Unless you intend to automate a new instance of Outlook, do not use the New or new keyword to create a new instance of Outlook, as this instance of the **Application** object is not trusted from the perspective of the Outlook Object Model Guard. 

If your add-in uses an untrusted instance of the **Application** object, depending on the version of Outlook that the client is running, the add-in by default will invoke Outlook's Object Model Guard on a number of members of the object model. 

For more information about the behavior of the Object Model Guard, see [Code Security Changes in Outlook 2007](https://msdn.microsoft.com/library/bb226709\(v=office.15\)). Note that even though the "Code Security Changes in Outlook 2007" article refers to COM add-ins that are trusted by default, this design applies to versions of Outlook since Outlook 2007, and the trust applies to managed add-ins the same way. Regardless of whether the add-in is managed or not, the trust is based on the assumption that the add-in uses a trusted **Application** object.

