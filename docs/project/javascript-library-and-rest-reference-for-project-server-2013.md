---
title: "JavaScript library and REST reference for Project Server 2013"

 
manager: soliver
ms.date: 8/10/2016
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 67b47b8b-d34b-4fad-af49-0c258c345ad2
description: "The JavaScript library and REST reference for Project Server 2013 contains information about the JavaScript object model and the REST interface that you use to access Project Server functionality. You can use these APIs to develop cross-browser web apps, Project Professional 2013 add-ins, and apps for non-Windows devices that access Project Server 2013 and Project Online."
---

# JavaScript library and REST reference for Project Server 2013

The JavaScript library and REST reference for Project Server 2013 contains information about the JavaScript object model and the REST interface that you use to access Project Server functionality. You can use these APIs to develop cross-browser web apps, Project Professional 2013 add-ins, and apps for non-Windows devices that access Project Server 2013 and Project Online.
  
> [!NOTE]
> The JavaScript object model and REST interface align with the Project Server client-side object model (CSOM). They provide equivalent functionality to the **Microsoft.ProjectServer.Client** namespace in the CSOM. 
  
You can access Project Server functionality through the JavaScript object model, which is defined in the [PS](http://msdn.microsoft.com/library/e3156167-a4fd-1bf6-8d1c-e180de1844ed%28Office.15%29.aspx) namespace in the  `%ProgramFiles%\Common Files\Microsoft Shared\Web Server Extensions\15\TEMPLATE\LAYOUTS\PS.js` file. The [ProjectContext](http://msdn.microsoft.com/library/a490b675-a845-ee94-3877-b99ada9bf2b0%28Office.15%29.aspx) object in the [PS](http://msdn.microsoft.com/library/e3156167-a4fd-1bf6-8d1c-e180de1844ed%28Office.15%29.aspx) namespace is the entry point to the JavaScript object model. 
  
> [!NOTE]
> To browse the JavaScript object model and to help with debugging, you can use the PS.debug.js file in the same directory. To help with development on a remote computer, the [Project 2013 SDK download](https://www.microsoft.com/en-us/download/details.aspx?id=30435) includes the .NET Framework assemblies for the CSOM, and the PS.js and PS.debug.js files. 
  
You can also access Project Server functionality through the REST interface. The entry point to the REST interface is the **ProjectServer** resource, which you access by using the  `http://ServerName/pwaName/_api/ProjectServer` endpoint URI. For example, the following query gets the assignments in the specified project (replace  _ServerName_ and  _pwaName_, and change the GUID to match a project).
  
```
http://ServerName/pwaName/_api/ProjectServer/Projects('263fc8d7-427c-e111-92fc-00155d3ba208')/Assignments
```

The **ProjectServer** resource is described in [ProjectServer resources in the REST interface](http://msdn.microsoft.com/library/a490b675-a845-ee94-3877-b99ada9bf2b0%28Office.15%29.aspx#bk_ProjectServerResources). Other REST resources are described in the documentation for the corresponding JavaScript objects and members in this reference. For more information about using REST, see [Client-side object model (CSOM) for Project Server](client-side-object-model-csom-for-project-2013.md) and [Programming using the SharePoint 2013 REST service](http://msdn.microsoft.com/en-us/library/fp142385%28office.15%29.aspx).
  
## JavaScript library and REST reference for Project Server
<a name="pj15_JavaScriptAPIReference_PS"> </a>

- [PS.js JavaScript library and REST reference](http://msdn.microsoft.com/library/5a140021-380a-d9e0-e36d-106df85f56d6%28Office.15%29.aspx) Contains information about the JavaScript object model and the REST interface for Project Server 2013. 
    
## See also
<a name="bk_addresources"> </a>

- [Project 2013 developer documentation](project-2013-developer-documentation.md)
    
- [Client-side object model (CSOM) for Project Server](client-side-object-model-csom-for-project-2013.md)
    
- [Getting started with the JavaScript object model](getting-started-with-the-project-server-2013-javascript-object-model.md)
    
- [How to: Work with projects by using the JavaScript object model](create-retrieve-update-and-delete-projects-using-the-project-server-javascript.md)
    

