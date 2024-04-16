---
title: Avoiding unsupported technologies in managed Outlook add-ins
TOCTitle: Avoiding unsupported technologies in managed Outlook add-ins
ms:assetid: 365fd319-725f-4c4b-b6e7-575f78ed8bda
ms:mtpsurl: https://msdn.microsoft.com/library/office/bb610014(v=office.15)
ms:contentKeyID: 55119789
ms.date: 07/24/2014
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Avoiding unsupported technologies in managed Outlook add-ins

Certain technologies that predate the .NET Framework are not supported in managed code programming. These technologies include Collaboration Data Objects (CDO), Messaging Application Programming Interface (MAPI, often known as Extended MAPI), and Simple MAPI. These technologies were designed and developed with unmanaged code, and Microsoft does not provide official managed wrappers to support their use in managed applications. 

## APIs that are supported in managed code

MAPI was originally designed and originally developed in the late 1980s. Therefore, MAPI predates managed code in the Microsoft .NET Framework. We do not provide managed wrappers for MAPI, and we discourage you from using third-party wrappers. This is because solutions may seem to work in a test environment, but issues that are related to memory management may occur when an application is deployed in a production environment and is exposed to real-world scalability scenarios.

The following table summarizes the support policy for Outlook APIs in the .NET Framework environment.

| API                                    |	DLL name	    | Managed code support policy |
| :--------------------------------------| :--------------| :---------------------------|
| Outlook object model	                 | Not applicable	| Supported by using a COM interop assembly |
| Collaboration Data Objects (CDO) 1.2x	 | Cdo.dll	      | Not supported |
| MAPI (Extended MAPI or Simple MAPI)    | Mapi32.dll or Msmapi32.dll	| Not supported |
| Exchange Server 2007 Web services	     | Not applicable	| Supported |
| WebDAV (Exchange 2000 Server and Exchange Server 2003, deprecated in Exchange Server 2007) | Not applicable	| Supported |

Nonetheless, Microsoft Outlook offers many object model features that achieve what previously only CDO and Exchange Client Extensions (ECE) solved for developers. If you use CDO in an existing unmanaged Outlook application and the lack of support for CDO in managed solutions has hindered you from migrating the application to managed code, you can now consider updating your solution to managed code, using only the Outlook object model and the Primary Interop Assembly (PIA), without having to resort to CDO. 

For more information about a more comprehensive Outlook platform introduced in Outlook 2007 to reduce reliance on CDO and ECE, see [What's New for Developers in Outlook 2007 (Part 1 of 2)](https://learn.microsoft.com/en-us/previous-versions/office/developer/office-2007/bb226711(v=office.12).
