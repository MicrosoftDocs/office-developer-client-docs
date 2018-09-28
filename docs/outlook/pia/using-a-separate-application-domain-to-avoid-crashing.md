---
title: Using a separate application domain to avoid crashing
TOCTitle: Using a separate application domain to avoid crashing
ms:assetid: 7fc6d1e5-7032-47a9-826f-6b5d3b43fef9
ms:contentKeyID: 55119786
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Using a separate application domain to avoid crashing

Managed add-ins that implement the **IDTExtensibility2** interface are loaded into the same default application domain. When an add-in in the application domain crashes, it can cause other add-ins in the same application domain to fail as well.

To work around this problem, you can create a shim for the add-in, so that the add-in can be loaded in its own application domain. A shim is an unmanaged dynamic link library written in C++. When you use a shim, you register the shim instead of the add-in. Outlook loads the shim, and the shim loads the add-in for which it was built. You must build and register a separate shim for each add-in. For more information about developing shims for managed add-ins, see [Isolating Office Extensions with the COM Shim Wizard](http://go.microsoft.com/fwlink/?linkid=89109).

Another alternative to load your add-in into a separate application domain is to develop your add-in using Office development tools in Visual Studio 2010, or a later release of Office Developer Tools for Visual Studio. Add-ins developed by these versions of Office Developer Tools for Visual Studio do not implement the IDTExtensibility2 interface but use the **IStartup** interface. They use a loader provided by Visual Studio, AddinLoader.dll, which acts like a generic shim. Outlook looks in the registry for add-ins created with Visual Studio. 

If Outlook finds such add-ins, Outlook starts AddinLoader.dll, which then starts the Visual Studio Tools for Office Runtime and relays the application manifest to the Visual Studio Tools for Office Runtime. The Visual Studio Tools for Office Runtime then loads each such add-in in a separate application domain. For more information about how Visual Studio loads an add-in, see [Architecture of Application-Level Add-Ins](https://msdn.microsoft.com/en-us/library/bb386298\(v=office.15\)).

