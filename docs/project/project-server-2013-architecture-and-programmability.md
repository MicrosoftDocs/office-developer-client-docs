---
title: "Project Server 2013 architecture and programmability"

 
manager: soliver
ms.date: 9/17/2015
ms.audience: Developer
 
f1_keywords:
- architecture
- platform
- Project
- Project architecture
- Project programmability
- Project Server architecture
- Project Server programmability
keywords:
- project 2013, architecture and programmability,Programmability, Project Server,Project 2013, benefits for EPM,Architecture, and Project Server
 
localization_priority: Normal
ms.assetid: 9ea3b3c1-fb90-454a-b8e6-abc44fca663d
description: "The articles in this section describe the overall architecture of the Enterprise Project Management (EPM) solution, which combines Project Professional 2013, Project Server 2013, Project Web App, and SharePoint Server 2013."
---

# Project Server 2013 architecture and programmability

The articles in this section describe the overall architecture of the Enterprise Project Management (EPM) solution, which combines Project Professional 2013, Project Server 2013, Project Web App, and SharePoint Server 2013.
  
Project Server 2013 is built with the .NET Framework 4 and is the third major release of Project Server to provide a true multitier architecture. For cloud access, Project Server 2013 implements a client-side object model (CSOM) and an OData service for reporting that can be used in web applications, mobile applications, and Silverlight applications. For applications on-premises, clients can use either the CSOM or the Project Server Interface (PSI) services. 
  
## Introduction to Project Server architecture

The topics in this section describe the overall architecture of the Enterprise Project Management (EPM) solution, which combines Project Professional 2013, Project Server 2013, Project Web App, and SharePoint Server 2013.
  
For programmatic access to Project Server, you should use either the CSOM or the PSI services with the Windows Communication Foundation (WCF) interface. The ASMX web service interface of the PSI is deprecated in Project Server 2013, but still works. The PSI enables efficient access by using datasets and you can create handlers for server-side events. The CSOM itself uses the PSI to access the Project Server business object layer. Instead of four Project Server databases, Project Server 2013 uses a single database in the data access layer.
  
Project Server 2013 integrates deeply with SharePoint Server 2013. The Project Application Service can be associated with other SharePoint site collections in the farm. Project Server can operate with and report on SharePoint task lists in the site collection, and can also get full control where Project Server imports and manages the task lists as enterprise projects. Project Server also uses version 4 of the Windows Workflow Foundation (WF4) and adds workflow activities for Demand Management solutions.
  
For a discussion of the many new features that Project 2013 provides for developers, and of the features that are deprecated, see [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md).
  
## In this section

[Project Server 2013 architecture](project-server-2013-architecture.md) describes the major parts of the Project 2013 platform, including the clients and servers. 
  
[Project Server programmability](project-server-programmability.md) discusses the main extensibility features of Project Server 2013, customization of Project Web App, and upgrading applications that are built for previous Project Server versions. 
  
[What the PSI does and does not do](what-the-psi-does-and-does-not-do.md) describes scenarios where the PSI can be used and lists things that the PSI cannot do. 
  
[What the CSOM does and does not do](what-the-csom-does-and-does-not-do.md) describes scenarios where the CSOM can be used and lists things that the CSOM cannot do. 
  
### Topics not covered

The articles in the  *Architecture and programmability*  section do not document features of the Project desktop clients (Project Standard 2013 and Project Professional 2013) or Project Web App. 
  
Visual Basic for Applications (VBA) help is available in the Visual Basic editor within Project Standard and Project Professional.
  
## See also
<a name="bk_addresources"> </a>

- [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md)
    
- [Getting started developing Project Server workflows](getting-started-developing-project-server-workflows.md)
    

