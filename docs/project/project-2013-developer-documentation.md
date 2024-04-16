---
title: "Project 2013 developer documentation"
manager: lindalu
ms.date: 02/22/2022
ms.audience: Developer 
f1_keywords:
- Project
- Project 2013
- Project 2013 SDK
- Project programmability
- Project SDK
- SDK
- SDK Project
keywords:
- sdk, project 2013,Project 2013, SDK overview 
ms.assetid: f66adbf1-5cb5-4dd0-be08-45e1c88c010c
description: "Find documentation, code samples, how-to articles, and programming references to help build apps for the Office or a private app catalog and to customize and integrate Project Server and the Project clients with a wide variety of other desktop and business applications for enterprise project management."
ms.localizationpriority: high
---

# Project 2013 developer documentation

Find documentation, code samples, how-to articles, and programming references to help build apps for AppSource. Learn how to customize and integrate Project Server and the Project clients with a wide variety of other desktop and business applications for enterprise project management (EPM).

> [!NOTE]
> Project Server 2013 is built on the SharePoint Server 2013 platform, and Project 2013 includes much of the same infrastructure as the other Office 2013 applications. For documentation of the model for SharePoint Add-ins, SharePoint-based workflows, Web Parts, development with other SharePoint features, and documentation of Office Add-ins, see [SharePoint Add-ins](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) and [Office Add-ins](/office/dev/add-ins/overview/office-add-ins).

## Introduction to the Project Software Development Kit (SDK)

Project Server 2013 is a platform for building on-premises or cloud-based enterprise project management solutions and for building apps that end users can discover and acquire through AppSource (formerly Office Store). The Project Server 2013 architecture is based on the platform introduced in Microsoft Office Project Server 2007, with many additions and improvements. The new features include a client-side object model (CSOM) to enable access to Project Online, an OData service for online access to Project Server reporting data, remote event receivers, workflow architecture that is based on version 4 of the Windows Workflow Foundation (WF4), and Office Add-ins, which is a common architecture for task pane extensions in Microsoft Office 2013 client applications.

A major change in Project Server 2013 is the use of a single database in place of the Draft, Published, Archive, and Reporting databases in Project Server 2010. For more information about new features and deprecated features, see [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md). For information about changes in the Project Server platform, see [Project Server 2013 architecture](project-server-2013-architecture.md). For an overview of the development platform that exists in Project Server 2010 and that Project Server 2013 is based on, see [Getting Started with Development for Project 2010](https://msdn.microsoft.com/library/gg607685.aspx) on MSDN.

Project Server 2013 is built on the Microsoft .NET Framework 4 and Microsoft SharePoint Server 2013. The articles and samples in this SDK provide a starting place for developing custom solutions and apps; they do not address all programmability features of Project Server or Project Professional. The [Project Developer Center](https://msdn.microsoft.com/library/4e5245c3-4891-455b-b321-1819cdd77247.aspx) includes links to Project articles, blogs, videos, webcasts, visual how-to articles, and other resources.

The Project 2013 SDK includes developer information for Project Server 2013, Project Web App, Project Professional 2013, and Project Standard 2013. The SDK articles are designed to help developers and administrators evaluate Project and Project Server for extensibility and plan for custom solutions.

### Welcome feedback

We would like to hear from you. In the online topics on MSDN, you can add comments, code samples, or flag the content as a bug in the **Community Content** section at the bottom of each page. When you install the Project 2013 SDK download, the local documentation articles each have a *Send Feedback* link that is located below the title. At any point in reading the SDK, choose the link to send an email to the SDK team. You can send corrections, a request for clarification or a code sample, or other comments, and help us make the content stronger.

### Download

The Project 2013 SDK download is available in the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=30435) The download includes Project2013SDK.HxS (the file that includes this article), related code samples, redistributable assemblies, and other resources. The Project 2013 SDK does not yet include the Reporting datatables reference.

### What's new in the Project SDK

<a name="pj15_Welcome_WhatsNew"> </a>

The main purpose of the Project 2013 SDK is to provide an overview of programmability and documentation of the CSOM and related features for creating apps, the Project Server Interface (PSI) services, and task pane apps for Project Professional 2013. The Project 2013 SDK includes step-by-step examples of key areas for customization of Project Server 2013 and the Project clients (Project Standard 2013, Project Professional 2013, and Project Web App). The documentation is incomplete; more content will be added in later releases.

The underlying technology for network communication is Windows Communication Foundation (WCF) in Project Server 2013, including cloud scenarios that use the Project Server CSOM and on-premises development using the PSI. The legacy ASMX web service references are also based on the WCF architecture. Setting a reference to a PSI web service (ASMX file) in Project Server 2013 requires appending the `?wsdl` URL option to the path. For example, `https://ServerName/ProjectServerName/_vti_bin/PSI/Resource.asmx?wsdl`.

> [!NOTE]
> Although it addresses only the most commonly used Project Server features, we recommend that you use the CSOM where possible for applications both on-premises and in the cloud. Although it is still available in Project Server 2013, the ASMX interface for the PSI is deprecated. For on-premises applications that require full access to the PSI, you should use the WCF interface for the PSI, rather than the ASMX interface.

Development on a Windows 7 computer is supported by copying the CSOM assemblies for Project Server 2013 and for SharePoint Server 2013 to the development computer. The SDK download includes the CSOM assemblies for Project Server and a redistribution license. To get the SharePoint CSOM assemblies, see [SharePoint Server 2013 Client Components SDK](https://www.microsoft.com/download/details.aspx?id=35585).

For development with the WCF services, you can set a reference to a PSI proxy assembly or add PSI proxy files to the solution. You can set direct references to the front-end Project Server ASMX web services from a remote computer within the same domain, or use a proxy assembly or proxy files. The SDK download includes proxy files for the WCF services and the ASMX web services, plus scripts for building the proxy assemblies and for generating updated proxy files.

In Project Server 2013, you can create declarative Project Server workflows by using Microsoft SharePoint Designer 2013, for both on-premises and online use. SharePoint Designer 2013 uses the workflow activity properties and methods in the CSOM. Development and deployment of Visual Studio 2012 solutions that include Project Server Web Parts, or customizations of Project Web App, is supported only on a Project Server computer.

For an overview of new programmability features and deprecated features in Project Server 2013, see [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md). Another major change in Project Server 2013 is the use of WF4-based workflows to manage the creation and approval of project proposals that are based on enterprise project templates.

New topics include the following:

- [Create a SharePoint-hosted Project Server add-in](create-a-sharepoint-hosted-project-server-add-in.md) shows how to use Visual Studio for remote development of an app that can be used with Project Server 2013 and Project Online.
- [Project Server 2013 architecture](project-server-2013-architecture.md) explains the major new features of the Project Server platform.
- [Getting started with the Project Server 2013 JavaScript object model](getting-started-with-the-project-server-2013-javascript-object-model.md) shows how to develop web applications that can access Project Server.
- [Getting started with the Project Server CSOM and .NET](getting-started-with-the-project-server-csom-and-net.md) shows how to use the client-side object model to develop applications, instead of using the PSI services.
- [Task pane apps for Project Professional](task-pane-add-ins-for-project.md) introduces Office Add-ins, as applied to Project 2013. The Office 2013 SDK includes articles that show how to develop task pane apps for Project and the other Office 2013 clients.
- [Create a Project Server workflow for Demand Management](create-a-project-server-workflow-for-demand-management.md) shows how SharePoint Designer 2013 can be used to create Project Server workflows.
- [ProjectData - Project OData service reference](https://msdn.microsoft.com/library/office/jj163015.aspx) includes an overview of the OData interface for Project Server reporting, plus XML reference topics for the **ProjectData** service.

Topics in the **Microsoft.ProjectServer.Client** namespace and new methods in the PSI services have only minimal documentation. Most of the reference topics for the PSI services are unchanged from the July 2011 release of the Project 2010 SDK.

### Future SDK releases

The Project 2013 SDK will be updated with new articles and reference content for the general availability release.

## Sections in the Project SDK

There are two top-level sections in the Project 2013 SDK:

- The [Project conceptual and how-to articles](project-conceptual-and-how-to-articles.md) section contains overviews of major features and articles with step-by-step procedures for development.

- The [Project Server 2013 class library and web service reference](https://msdn.microsoft.com/library/ef1830e0-3c9a-4f98-aa0a-5556c298e7d1%28Office.15%29.aspx) section documents the object model of the public assemblies, the Microsoft.ProjectServer.Client.dll assembly for the CSOM, and the PSI services.

The **Conceptual and how-to articles** section includes the following:

- [What's new and what's out for developers](updates-for-developers-in-project-2013.md) describes the major new programmability features and deprecated features in Project 2013.

- [Project overview for developers](https://msdn.microsoft.com/library/8da91ab0-af4f-429f-8241-490600e3f7bd%28Office.15%29.aspx) includes articles about Project Server architecture, articles that show how to get started developing with the CSOM, information about new features in VBA for Project, and a reference to the Office 2013 SDK, which contains topics about developing task pane apps for Project Professional 2013.

- [Project programming tasks](project-programming-tasks.md) includes how-to articles about creating apps for Project Server, using JavaScript with the CSOM, and creating project proposals and workflows for demand management.

- [Project 2013 programming references](project-2013-programming-references.md) includes an introduction to the PSI reference for Project Server 2013, information about Project Server error codes, and the OData schema reference for the **ProjectData** service.

> [!NOTE]
> Following are requirements to develop and deploy EPM solutions and apps from AppSource that integrate with Project Server 2013:
> You must install either the .NET Framework 4 or the .NET Framework 4.5 on the development computer and on the deployment computers. To determine whether the correct release is installed, open **Programs and Features** in the Windows Control Panel.
> Visual Studio 2012 installs and uses the .NET Framework 4.5. When you create a Visual Studio project, you can select either **.NET Framework 4.0** or **NET Framework 4.5** in the drop-down list of the **New Project** dialog box. You can also select the **Target Framework** on the **Application** tab of the project **Properties** window.
> You can use Visual Studio 2010 for applications that use the CSOM or the PSI, and for Project task pane apps. However, Visual Studio 2010 does not contain the Office Add-ins templates, Office development tools, or SharePoint development tools for Office 2013. To download Visual Studio 2012 and the Web Platform Installer (WebPI) that includes the Office and SharePoint development tools, see [Downloads for Apps for Office and SharePoint](https://msdn.microsoft.com/office/apps/fp123627).
> We recommend that you develop custom solutions in a test environment. If you develop solutions for the current builds of Project Server 2013 and Project 2013, they should be recompiled with updated references, and may need additional changes, to work with later releases. Solutions developed for any pre-release version may not work with the released version.

## See also

<a name="pj15_Welcome_AR"> </a>

- [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md)
- [Project Server 2013 architecture](project-server-2013-architecture.md)
- [Project 2013 SDK download](https://www.microsoft.com/download/details.aspx?id=30435%20)
- [SharePoint Server 2013 Client Components SDK](https://www.microsoft.com/download/details.aspx?id=35585)
- [Project for developers](https://msdn.microsoft.com/project)
- [Office Developer Documentation](https://msdn.microsoft.com/office)
- [Getting Started with Development for Project 2010](https://msdn.microsoft.com/library/gg607685.aspx)
- [Document conventions](https://msdn.microsoft.com/library/6b38829f-1a9d-4fb6-ad3b-01182628080a.aspx)
- [Accessibility in SharePoint 2013](https://msdn.microsoft.com/library/jj841103.aspx)
- [Accessibility in Microsoft Office 365](https://www.microsoft.com/enable/products/office365/)
- [Microsoft online privacy notice](https://privacy.microsoft.com/privacystatement)
