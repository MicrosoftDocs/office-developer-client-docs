---
title: Why use the Outlook PIA
TOCTitle: Why use the Outlook PIA
ms:assetid: 5cc9085e-7c97-4698-8cb9-e33e427c02e7
ms:contentKeyID: 55119773
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Why use the Outlook PIA

Starting in Outlook 98, Outlook provides an object model for developers to integrate Outlook functionality into an application, extend Outlook, or automate Outlook. This object model is designed to work with the Component Object Model (COM) technology. Historically, Outlook application developers developed COM solutions by using Visual Basic for Applications (VBA) and Visual Basic. However, Outlook solutions developed with VBA have deployment limitations, particularly in corporate environments, and are difficult to update after they are deployed.

The .NET Framework provides a rich set of class libraries and support technologies that address many of the limitations of VBA and COM add-ins. However, a managed application needs a bridge between the .NET and COM environments in order to program against a COM object model. An interop assembly is a COM wrapper that acts as the bridge. Consequently, more Outlook solutions are now developed as managed applications that rely on an interop assembly. For more information about how interop assemblies facilitate interoperability between .NET and COM, see [Introduction to interoperability between COM and .NET](introduction-to-interoperability-between-com-and-net.md).

An interop assembly describes COM types and enables managed code to interact with a COM object model. Any number of interop assemblies can exist to describe a given COM type. As publisher of the type library, Outlook provides a Primary Interop Assembly (PIA) that contains the official description of the COM-based Outlook object model. In general, it is best to use the Outlook PIA rather than relying on an interop assembly from another source.

## Using Visual Studio and Office Developer Tools for Visual Studio

It is possible for developers to create managed Outlook solutions outside of Visual Studio, but using Visual Studio makes integrating Outlook functionality into managed code much easier. The convenience and ease of development makes it more favorable for add-in developers to migrate from COM to .NET development. At design time, developers can use Office Developer Tools for Visual Studio to create add-ins that have access to both the Outlook object model and the .NET Framework. At run time, Office Developer Tools for Visual Studio provide a loader for these add-ins: when a user starts Outlook, this loader starts the common language runtime (CLR), the Visual Studio Tools for Office Runtime, and then loads the add-in assembly. The assembly can capture events raised in Outlook.

Visual Studio 2012 installs the add-in templates for Office 2010 by default. To use Office Developer Tools for Visual Studio to develop managed add-ins for Outlook 2013, you must [download](https://aka.ms/officedevtoolsforvs2012) the templates for Office 2013.

For more information about Office Developer Tools for Visual Studio, see [Configure a computer to develop Office solutions](https://docs.microsoft.com/visualstudio/vsto/how-to-configure-a-computer-to-develop-office-solutions?view=vs-2017). For more information about programming managed add-ins for Outlook, see [Get started programming VSTO Add-ins](https://docs.microsoft.com/visualstudio/vsto/getting-started-programming-vsto-add-ins?view=vs-2017).

## See also

- [Installing and referencing the Outlook PIA](installing-and-referencing-the-outlook-pia.md)

