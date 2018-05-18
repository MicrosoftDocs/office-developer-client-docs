---
title: "Client-side object model (CSOM) for Project 2013"

 
manager: soliver
ms.date: 8/10/2016
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 716325eb-b092-4934-921f-84129d0a1f5f
description: "The Project Server 2013 client-side object model (CSOM) implements common server functionality. The Project Server CSOM includes a Microsoft .NET CSOM, a Microsoft Silverlight CSOM, a Windows Phone 8 CSOM, and a JavaScript object model (JSOM). In addition, the CSOM includes an OData service that enables a REST interface. The REST interface is intended primarily for development of apps on non-Windows platforms such as iOS and Android."
---

# Client-side object model (CSOM) for Project 2013

The Project Server 2013 client-side object model (CSOM) implements common server functionality. The Project Server CSOM includes a Microsoft .NET CSOM, a Microsoft Silverlight CSOM, a Windows Phone 8 CSOM, and a JavaScript object model (JSOM). In addition, the CSOM includes an OData service that enables a REST interface. The REST interface is intended primarily for development of apps on non-Windows platforms such as iOS and Android.
  
> [!NOTE]
> Solutions for Project Online must use the CSOM. However, on-premises apps can use either the CSOM or the Project Server Interface (PSI). If the CSOM includes the functionality you plan to use, we recommend that you use the CSOM for new apps. 
  
In CSOM extensions, the **ProjectContext** object provides the entry point to server content and functionality. The .NET CSOM, the Silverlight CSOM, and the Windows Phone CSOM use the [Microsoft.ProjectServer.Client.ProjectContext](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.aspx) object, and the JSOM uses the **PS.ProjectContext** object. **ProjectContext** properties provide direct access to core Project Server objects in the current Project Web App site collection. For information about the location of the CSOM assemblies and the JavaScript file, see [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx) . 
  
 **Apps and the security model** Apps must use the CSOM for CRUD (create, read, update, delete) operations with Project Server 2013 and Project Online. Project apps do not use the app-only authentication model in SharePoint 2013. A Project Server app requires a specific permission request scope that specifies on whose behalf commands are being run. 
  
 **REST queries** You can create REST queries of the CSOM OData service without consuming the metadata. Some third-party tools enable using the .NET assemblies for the CSOM to develop apps for other devices. For example, search the Internet for "cross-platform .NET development tools for iOS or Android." 
  
> [!NOTE]
> Although the  `$metadata` option for the **ProjectData** reporting service is valid (  `http://ServerName/pwaName/_api/ProjectData/$metadata`), the  `$metadata` option for the **ProjectServer** service of the CSOM is removed in the released version of Project Server 2013. To find the CSOM objects and members that are available as REST endpoints, see the [JavaScript library and REST reference for Project Server 2013](javascript-library-and-rest-reference-for-project-server-2013.md). 
  
To see the entities available in the CSOM through the REST interface, you can use the  `http://ServerName/pwaName/_api/ProjectServer` query. For REST queries, the **ProjectServer** entity closely mirrors properties of the [ProjectContext](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.aspx) object in the Microsoft.ProjectServer.Client.dll managed assembly and the [PS.ProjectContext](http://msdn.microsoft.com/library/a490b675-a845-ee94-3877-b99ada9bf2b0%28Office.15%29.aspx) object in the JSOM. For example, you can use your browser to get information from the CSOM about projects in Project Web App, the assignments in a specified project, and the task name of a specified assignment for a specified resource, by using the following queries (each query uses the same  `http://ServerName/pwaName/_api` URL prefix). The GUIDs are sample values for **Project.Id**, **EnterpriseResource.Id**, and **Assignment.Id**.
  
```HTML
/ProjectServer/Projects
/ProjectServer/Projects('263fc8d7-427c-e111-92fc-00155d3ba208')/Assignments
/ProjectServer/EnterpriseResources('28eeb2b5-fe74-4efc-aa35-6a64514d1526')/Assignments('a2eafeb5-437c-e111-92fc-00155d3ba208')/Task?$select=Name
```

Unlike the OData interface for the **ProjectData** service, which is read-only for reporting, you can do CRUD operations using REST queries with the **ProjectServer** service. REST queries for the Project Server CSOM are designed primarily for platforms other than the Windows desktop, such as Windows RT, iOS, and Android. For Windows desktop and server platforms, such as Windows 7, Windows 8, and Windows Server 2008 R2, you can use the CSOM managed assemblies. For web apps, you can use PS.js for JavaScript. For information about doing CRUD operations using REST queries, see the [Use OData query operations in SharePoint REST requests](http://msdn.microsoft.com/library/d4b5c277-ed50-420c-8a9b-860342284b72%28Office.15%29.aspx) topic in the SharePoint 2013 SDK. For information about using the **ProjectData** service, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
Table 1 lists the **ProjectContext** properties that represent Project Server objects. You can use these objects to retrieve other Project Server 2013 entities, such as assignments and tasks. 
  
**Table 1. ProjectContext properties that provide access to Project Server objects in the CSOM and JSOM**

|**CSOM (.NET, Silverlight, and Windows Phone)**|**JSOM**|
|:-----|:-----|
|[CustomFields](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.CustomFields.aspx) <br/> |customFields  <br/> |
|[EnterpriseProjectTypes](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.EnterpriseProjectTypes.aspx) <br/> |enterpriseProjectTypes  <br/> |
|[EnterpriseResources](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.EnterpriseResources.aspx) <br/> |enterpriseResources  <br/> |
|[EntityTypes](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.EntityTypes.aspx) <br/> |entityTypes  <br/> |
|[EventHandlers](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.EventHandlers.aspx) <br/> |eventHandlers  <br/> |
|[Events](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.Events.aspx) <br/> |events  <br/> |
|[LookupTables](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.LookupTables.aspx) <br/> |lookupTables  <br/> |
|[Phases](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.Phases.aspx) <br/> |phases  <br/> |
|[Projects](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.Projects.aspx) <br/> |projects  <br/> |
|[Stages](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.Stages.aspx) <br/> |stages  <br/> |
|[WorkflowActivities](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.WorkflowActivities.aspx) <br/> |workflowActivities  <br/> |
|[WorkflowDesigner](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.WorkflowDesigner.aspx) <br/> |workflowDesigner  <br/> |
   
## In this section

[Getting started with the Project Server CSOM and .NET](getting-started-with-the-project-server-csom-and-net.md) provides overview information about the Project Server CSOM and .NET, instructions about how to create a simple .NET CSOM extension in Visual Studio 2012, and supporting code examples. 
  
[Getting started with the Project Server 2013 JavaScript object model](getting-started-with-the-project-server-2013-javascript-object-model.md) provides overview information about the Project Server JSOM, instructions about how to create a simple JSOM extension in Visual Studio 2012, and supporting code examples. 
  
Also, check out these articles that show how to use the CSOM:
  
- [Bulk update custom fields and create project sites from a workflow in Project Online](bulk-update-custom-fields-and-create-project-sites-from-a-workflow-in-project.md)
    
- [Work with projects by using the JavaScript object model](create-retrieve-update-and-delete-projects-using-the-project-server-javascript.md)
    
> [!NOTE]
> You can also use Visual Studio 2010 for .NET Framework 4 development with the CSOM. 
  
## Reference

[Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx)
  
## See also



[Project Server 2013 architecture](project-server-2013-architecture.md)


[Choose the right API set in SharePoint 2013](http://msdn.microsoft.com/library/f36645da-77c5-47f1-a2ca-13d4b62b320d%28Office.15%29.aspx)

