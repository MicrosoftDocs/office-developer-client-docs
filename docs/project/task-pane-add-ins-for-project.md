---
title: "Task pane add-ins for Project"

 
manager: soliver
ms.date: 09/10/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 44712b7c-aead-433d-8c0e-76407264166c
description: "Project Standard 2013 and Project Professional 2013 both support task pane Office Add-ins. You can use task pane add-ins to integrate project, task, resource, and view data in a project with other Office 2013 client applications, SharePoint applications, Web Parts, other webpages, and external data."
---

# Task pane add-ins for Project

Project Standard 2013 and Project Professional 2013 both support task pane Office Add-ins. You can use task pane add-ins to integrate project, task, resource, and view data in a project with other Office 2013 client applications, SharePoint applications, Web Parts, other webpages, and external data.
  
Office Add-ins is an extensibility model that is supported in several Office 2013 client applications. The full add-in platform includes contextual, content, and task pane add-in types. Outlook 2013 supports mail add-ins, which can show a webpage within an email message or calendar appointment item that is related to content in the item. Word 2013 and Excel 2013 support content add-ins, which can show a webpage as embedded content in a document. Word 2013, Excel 2013, and Project Professional 2013 support task pane add-ins, which can show a webpage in a task pane where the content is related to contextual information within the project.
  
For example, a Project add-in can summarize data in the active project and show additional data about a selected task or resource. Related data in the add-in can come from an external source such as a SharePoint list, reporting tables in the Project Server database, a web service, or another enterprise application. A task pane add-in can be developed with HTML 5, JavaScript, JQuery and other JavaScript libraries. A task pane add-in does not directly support ActiveX, Silverlight, or Flash components. Although an Office Add-in could use an **IFrame** element to access a server-side web application that uses ASP.NET and the .NET Framework 4.5 library, that kind of solution is not recommended or supported. The add-in can be developed to save data locally or write data to an external location. 
  
> [!NOTE]
> Task pane Project Add-ins can access data from Project Online by using OAuth authentication. With Project Professional 2013, you can develop task pane add-ins that access both on-premises installations of Project Server 2013 and on-premises or online SharePoint 2013. For example, see [Connecting a Project Task Pane add-in to PWA](https://blogs.msdn.com/b/project_programmability/archive/2012/11/02/connecting-a-project-task-pane-app-to-pwa.aspx) in the Project Programmibility blog. > Project Standard 2013 does not support direct integration with Project Server data or SharePoint task lists that are synchronized with Project Server. 
  
For more information about add-ins for Office 2013, see [Office and SharePoint Add-ins](https://msdn.microsoft.com/library/office/fp161507%28v=office.15%29). 
  
## Developing task pane add-ins

The developer documentation for Office and SharePoint Add-ins includes comprehensive articles and references. For an introduction to developing add-ins for Project Professional 2013 and other Office 2013 client applications, and for the JavaScript reference and XML manifest reference, see [Office Add-ins](https://msdn.microsoft.com/library/office/apps/jj220060%28v=office.15%29).
  
The Project 2013 SDK download includes the **Project OM Test** sample add-in that shows how to get the GUID of a task, resource, and view, how to get properties of the active project, and how to set a task, resource, or view selection changed event handler. When you extract and install the SDK and samples in the Project2013SDK.msi file, see the  `\Samples\Apps\Copy_to_AppSource_FileShare` subdirectory and the  `\Samples\Apps\Copy_to_AppManifests_FileShare` subdirectory. The JSOMCall.html sample uses JavaScript functions in the office.js file and project-15.js file, which are included in the download. You can use the corresponding debug files (office.debug.js and project-15.debug.js) to examine the functions. 
  
The **HelloProject_OData** sample add-in for Project Professional 2013 was developed with Visual Studio 2012. The add-in uses a REST query of the **ProjectData** service to get reporting data for project cost and other information, and then compares the current project with the average values for all projects in Project Web App. 
  
## See also
<a name="bk_addresources"> </a>

- [Task pane add-ins for Project](https://msdn.microsoft.com/library/office/apps/fp161143%28v=office.15%29)
    
- [Connecting a Project Task Pane add-in to PWA](https://blogs.msdn.com/b/project_programmability/archive/2012/11/02/connecting-a-project-task-pane-app-to-pwa.aspx)
    
- [Project 2013 SDK download](https://www.microsoft.com/en-us/download/details.aspx?id=30435%20)
    
- [Office and SharePoint Add-ins](https://msdn.microsoft.com/library/office/fp161507%28v=office.15%29)
    
- [Office Add-ins](https://msdn.microsoft.com/library/office/apps/jj220060%28v=office.15%29)
    

