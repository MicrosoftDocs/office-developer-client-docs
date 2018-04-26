---
title: "What the CSOM does and does not do"

 
manager: soliver
ms.date: 9/17/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6828485c-040b-4278-923f-4cc7c8fe0fb1
description: "The client-side object model (CSOM) is a set of APIs for Project Server 2013 that are designed for both online and on-premises use in apps that can be developed for PCs, mobile devices, and tablets. This article includes some typical scenarios for using the CSOM and also lists limitations of the CSOM."
---

# What the CSOM does and does not do

The client-side object model (CSOM) is a set of APIs for Project Server 2013 that are designed for both online and on-premises use in apps that can be developed for PCs, mobile devices, and tablets. This article includes some typical scenarios for using the CSOM and also lists limitations of the CSOM.
  
|||
|:-----|:-----|
|||
   
The CSOM enables the development of apps for Project Server 2013 and integration of Project Server with other applications. The apps can be developed to run on PCs, mobile devices such as Windows Phone 7.5, tablets such as Windows 8 devices, and iOS and Android devices. The CSOM provides APIs that cover functionality of the twelve most commonly used PSI services in Project Server. The CSOM APIs are organized differently and are easier to use than the ASMX-based and WCF-based PSI services. The CSOM does not use ADO.NET datasets and is accessible through the OData protocol. You can develop with the CSOM by using .NET Framework 4 libraries, JavaScript, or Representational State Transfer (REST) queries.
  
For an overview of the CSOM and articles that show how to use JavaScript and .NET Framework 4 with the CSOM, see [Client-side object model (CSOM) for Project Server](client-side-object-model-csom-for-project-2013.md). For more information about the CSOM assemblies, classes, and members, see the [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx) namespace reference. 
  
## Usage scenarios for the CSOM
<a name="pj15_WhatTheCSOM_UsageScenarios"> </a>

Following are examples of some kinds of apps that the CSOM supports. The CSOM can be used instead of the PSI for many scenarios:
  
- **Develop apps that extend Project Server** The primary purpose of the CSOM is app development for Project Server 2013, where apps can be created for a wide variety of devices that include PCs, mobile devices, and tablets. Apps can be distributed within a private app catalog or in the public Office Store. 
    
- **Automate the creation or management of entities in Project Server** The CSOM can perform CRUD operations for entities such as projects, tasks, assignments, enterprise resources, custom fields, lookup tables, timesheets, event handlers, and workflow phases and stages. There are often cases where a custom app can save time with bulk or repetitive jobs. 
    
- **Get data in the published tables of the Project database** Because direct database access to the draft, published, and archive tables is not supported, you can use the CSOM to read data that is not available in the reporting tables or views. For example, get information about workflow stages, phases, and activities. To read data in the reporting tables, you can use OData queries. 
    
- **Validate statusing and timesheet data** Use the CSOM in local event handlers or remote event receivers for pre-events to validate assignment status or timesheet data that users enter, before the data is saved in Project Web App. 
    
- **Create financial projects** Create projects for time capture through the timesheet for integration with a financial system. Create a hierarchy of financial codes that reflect the cost breakdown structure of the financial system. Financial projects do not require scheduling or status updates. 
    
- **Integrate with accounting systems** Capture the resource costs and expenses associated with projects to feed financial and billing systems and for budget comparison purposes. Synchronize tasks, resources, and assignments between the systems. Capture timesheet data in one system to feed the other (which timesheet is used depends on the needs of the organization or of individual projects). 
    
- **Automate updates from team members** For projects that are not actively managed, automatically update projects on the server with progress and other changes from project team members. Projects can be updated and republished without a project manager reviewing the results or making adjustments to the plan. 
    
    > [!NOTE]
    > The CSOM supports submitting status updates, but currently does not support status approvals. 
  
- **Evaluate Project Server data in remote event receivers** A remote event receiver for a **ProjectCreating** pre-event can use Project Server data from the CSOM to help determine whether to cancel the event. For example, before creating a project, compare the project proposal with existing projects. 
    
- **Support declarative Project Server workflows** The CSOM enables Project Server workflows that are created in SharePoint Designer 2013. The CSOM supports workflow definitions that use Windows Workflow Foundation version 4 (WF4). (The PSI does not support WF4 workflows.) 
    
- **Create complex Project Server workflows** When you develop workflows with Visual Studio 2012, you can use the CSOM for complex actions within workflow stages or create custom workflow actions. 
    
## What the CSOM does not do
<a name="pj15_WhatTheCSOM_DoesNotDo"> </a>

The CSOM is not a complete replacement for the PSI. Because the CSOM internally uses the PSI services, the CSOM has many of the same functional limitations that the PSI has. In addition to limitations of the PSI, such as having no access to data in local projects (.mpp files), the CSOM does not include administrative functionality that Project Web App typically handles. For example, creating custom security groups can be handled in the Site Settings - Permissions page for Project Web App. 
  
For a list of actions that neither the PSI nor the CSOM handle, see the  *What the PSI does not do*  section in [What the PSI does and does not do](what-the-psi-does-and-does-not-do.md).
  
### PSI services that the CSOM does not cover
<a name="pj15_WhatTheCSOM_PSIServices"> </a>

The CSOM does not include functionality of the following PSI services:
  
- **Admin service** To manage administrative settings and operations in Project Server and for related project sites, such as creating fiscal periods and making timesheet settings, use PSI methods in the [WebSvcAdmin.Admin](https://msdn.microsoft.com/library/WebSvcAdmin.Admin.aspx) class. Project Web App itself uses **Admin** methods in many of the pages that are linked to the Server Settings page (http://  *ServerName*  /  *ProjectServerName*  /_layouts/15/pwa/Admin/Admin.aspx). 
    
- **Archive service** To save and manage entities such as projects, resources, and custom fields in the archive tables, use PSI methods in the [Archive](https://msdn.microsoft.com/library/WebSvcArchive.Archive.aspx) class. 
    
- **CubeAdmin service** To create and manage OLAP cubes for on-premises installations, use PSI methods in the [WebSvcCubeAdmin.CubeAdmin](https://msdn.microsoft.com/library/WebSvcCubeAdmin.CubeAdmin.aspx) class, or use the OLAP Database Management page (http://  *ServerName*  /  *ProjectServerName*  /_layouts/15/pwa/CubeAdmin/CubeAnalysisAdmin.aspx) in Project Web App. 
    
    > [!NOTE]
    > Project Online does not support OLAP cubes. 
  
- **Driver service** To create and manage business drivers for project portfolio analyses, use PSI methods in the [WebSvcDriver.Driver](https://msdn.microsoft.com/library/WebSvcDriver.Driver.aspx) class. 
    
- **LoginForms service and LoginWindows service** Authentication in the CSOM is done during initialization of the **ProjectContext** object, with OAuth or Windows authentication. To create applications for multi-authentication, where a local full-trust application can use both Forms authentication and Windows authentication, use PSI methods in the [WebSvcLoginForms.LoginForms](https://msdn.microsoft.com/library/WebSvcLoginForms.LoginForms.aspx) class and the [WebSvcLoginWindows.LoginWindows](https://msdn.microsoft.com/library/WebSvcLoginWindows.LoginWindows.aspx) class. 
    
- **Notification service** To create and manage alerts and reminders, use PSI methods in the [WebSvcNotifications.Notifications](https://msdn.microsoft.com/library/WebSvcNotifications.Notifications.aspx) class. 
    
- **ObjectLinkProvider service** To create and manage web objects and links to documents and SharePoint list items, use PSI methods in the [WebSvcObjectLinkProvider.ObjectLinkProvider](https://msdn.microsoft.com/library/WebSvcObjectLinkProvider.ObjectLinkProvider.aspx) class. 
    
- **PortfolioAnalyses service** To create and manage project portfolio analyses, including planner solutions and optimizer solutions, use PSI methods in the [WebSvcPortfolioAnalyses.PortfolioAnalyses](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.aspx) class. 
    
- **QueueSystem service** The CSOM can get basic information about Project Server queue jobs, and includes the [ProjectContext.WaitForQueue](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.WaitForQueue.aspx) method. For more extensive management of the Project Server Queuing System, use PSI methods in the [WebSvcQueueSystem.QueueSystem](https://msdn.microsoft.com/library/WebSvcQueueSystem.QueueSystem.aspx) class. 
    
- **Security service** To create and manage Project Server security groups, templates, and categories, and to check permissions for the current user, use PSI methods in the [WebSvcSecurity.Security](https://msdn.microsoft.com/library/WebSvcSecurity.Security.aspx) class. 
    
- **WssInterop service** To get information about and manage project sites, use PSI methods in the [WebSvcWssInterop.WssInterop](https://msdn.microsoft.com/library/WebSvcWssInterop.WssInterop.aspx) class. 
    
    > [!NOTE]
    > You can use the CSOM in SharePoint Server 2013. Project sites are SharePoint sites. 
  
The CSOM does not enable extensions such as the PSI can have. For example, if you create a PSI extension for local use, the CSOM cannot be modified to use the PSI extension. You can implement extension scenarios in other ways:
  
- Aggregate CSOM calls within a local component or a component that runs on Microsoft Azure.
    
- Use OData queries of the reporting data, instead of directly accessing reporting tables in the Project Server database.
    
- Integrate CSOM calls with third-party applications through OAuth authentication from Project Online or with server-side components for on-premises use.
    
- Applications that use the CSOM can also use custom databases either on-premises or with SQL Azure.
    
### Request limits of the CSOM
<a name="pj15_WhatTheCSOM_RequestLimits"> </a>

The CSOM in Project Server 2013 is built on the CSOM implementation in SharePoint Server 2013 and inherits the limits for the maximum size of a request. SharePoint has a 2 MB limit for an operations request, and a 50 MB limit for the size of a submitted binary object. The request size is limited to protect the server from excessively long queues of operations and from processing delays for large binary objects.
  
For example, if you use the CSOM to create a project, and then edit the project to add 252 tasks with a minimum amount of information such as a short name, the task GUID, and a duration of 1d, the total amount of data in the **DraftProject.Update** request is less than 2 MB. But, if you try to add 253 such tasks to an empty project, the 2 MB limit is exceeded, and you get the following exception: **Microsoft.SharePoint.Client.ServerException: The request uses too many resources**
  
To capture the data in a CSOM request over HTTP or HTTPS, you can use a web debugging tool such as [Fiddler](http://www.fiddler2.com) (http://www.fiddler2.com). For a code example that implements a test for request size and includes a solution that breaks a large request into to smaller groups, see [DraftProject.Update](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.DraftProject.Update.aspx) . 
  
## Additional resources
<a name="pj15_WhatTheCSOM_AR"> </a>

- [Client-side object model (CSOM) for Project Server](client-side-object-model-csom-for-project-2013.md)
    
- [What the PSI does and does not do](what-the-psi-does-and-does-not-do.md)
    
- [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx)
    

