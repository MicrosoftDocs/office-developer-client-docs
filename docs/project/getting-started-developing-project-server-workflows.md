---
title: "Getting started developing Project Server workflows"

 
manager: lindalu
ms.date: 08/10/2016
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: 735bbb04-a8c1-46c0-a346-42050f0ac9b1
description: "Demand management processes in Project Server 2013 include workflows that help you manage project proposals and portfolio analyses. This section includes articles that show how to create workflows for Project Server."
---

# Getting started developing Project Server workflows

Demand management processes in Project Server 2013 include workflows that help you manage project proposals and portfolio analyses. This section includes articles that show how to create workflows for Project Server.
  
Project Server 2013 workflows use the SharePoint Server 2013 workflow platform, which is built on version 4 of Windows Workflow Foundation (WF4). WF4-based workflows are declarative, which means that the workflow design tool saves workflow stages, actions, conditions, and other elements to XAML code, which is interpreted at run-time. You can use either SharePoint Designer 2013 or Visual Studio 2012 to create declarative workflows. A workflow requires the Workflow Manager Client 1.0 execution engine, which can be on a local server for on-premises solutions or on a remote server for Project Online solutions.
  
You can use SharePoint Designer 2013 to create relatively simple declarative workflows. For complex workflows, and workflow templates that can be reused, you can use Visual Studio 2012 to develop and debug workflows for Project Web App. For more information, see [Creating Project Workflows using Visual Studio 2012](https://blogs.msdn.com/b/project_programmability/archive/2012/11/07/creating-project-workflows-using-visual-studio-2012.aspx).
  
> [!IMPORTANT]
> Use a test installation of Project Server, not a production installation, to develop and test workflows. Workflows that are developed for pre-release versions of Project Server 2013 must be tested for the release version, and may have to be created again and redeployed. 
  
## In this section

[Create a Project Server workflow for Demand Management](create-a-project-server-workflow-for-demand-management.md)
  
## See also



[Bulk update custom fields and create project sites from a Project Online workflow](bulk-update-custom-fields-and-create-project-sites-from-workflow-in-project.md)


[Workflow development in SharePoint Designer 2013 and Visio 2013](https://msdn.microsoft.com/library/jj163272%28office.15%29.aspx)
  
[What's new in workflows for SharePoint 2013](https://msdn.microsoft.com/library/jj163177.aspx)
  
[Develop SharePoint 2013 workflows using Visual Studio](https://msdn.microsoft.com/library/jj163199.aspx)
  
[Creating Project Workflows using Visual Studio 2012](https://blogs.msdn.com/b/project_programmability/archive/2012/11/07/creating-project-workflows-using-visual-studio-2012.aspx)
  
[Windows Workflow Foundation](https://msdn.microsoft.com/library/dd489441.aspx)
  
[A developer's introduction to Windows Workflow Foundation (WF) in .NET 4](https://msdn.microsoft.com/library/ee342461.aspx)
  
[Hitchhiker's guide to demand management (white paper)](https://msdn.microsoft.com/library/ff973112.aspx)

