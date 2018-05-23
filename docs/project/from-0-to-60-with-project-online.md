---
title: "From 0 to 60 with Project Online"
manager: soliver
ms.date: 11/8/2016
ms.audience: Developer
localization_priority: Normal
ms.assetid: 5b48958e-6dab-4121-871f-fb15f58f1b24
description: "An application developer can customize a Project Online site (SharePoint hosted) using standalone applications and/or Project add-ins. A wealth of applications is possible that range from addressing needs of those involved in a project to PMO support functions, such as any of the following:"
---

# From 0 to 60 with Project Online

An application developer can customize a Project Online site (SharePoint hosted) using standalone applications and/or Project add-ins. A wealth of applications is possible that range from addressing needs of those involved in a project to PMO support functions, such as any of the following:
  
- Streamlined timecard data entry for workers
- Efficient timecard approval for supervisors
- Oversight of permits (procurement and status) needed for a project
- Status/Health check of active projects
- Issues report
- Change Management Status report
    
Project Online includes API support to accommodate the following scenarios:
  
- For a Project (SharePoint) hosted add-in:
    
  - Code (JavaScript, HTML, CSS) that is hosted in SharePoint Online
  - Assets that are downloaded to the browser and executed against SharePoint Online.  
  - Business logic that is in JavaScript   
  - Access data that is in/stored in Project Online or SharePoint such as (but is not limited to):  
  - Custom fields  
  - Lists
    
- For a Project (SharePoint) provider-hosted add-in:
    
  - Code that exists on a site external to the Project Online site 
  - An external site, which can be (but is not limited to):  
  - Another SharePoint site  
  - Web App/Service built on any platform  
  - The external site contains business logic  
  - The browser is redirected from Project Online to external site with access tokens to Project Online  
  - The external site can make calls to SharePoint and Project Online
    
- For an external/standalone add-in:
    
  - User executes an application on their device
  - Application authenticates and calls Project Online APIs directly
    

|Type of application|API implementation|Target environment|Application examples|
|:-----|:-----|:-----|:-----|
|Project hosted  <br/> |JSOM (Java Script Object Model)  <br/> REST  <br/> |Browser  <br/> |Timecard entry  <br/> Timecard approval  <br/> Project Status  <br/> Issues Report  <br/> |
|Project Provider Hosted  <br/> |CSOM client library  <br/> |Azure Website/App  <br/> Non-Windows environment (LAMP, etc.)  <br/> |External timesheet validator  <br/> Project Importer  <br/> |
|External/Standalone  <br/> |REST  <br/> CSOM  <br/> |REST - any platform  <br/> CSOM - any .NET supported platform  <br/> |Timecard entry  <br/> Migration of projects to a new site  <br/> Change Management Status.  <br/> |
   
## What does it take to start developing applications for Project Online?

The common items needed for developing Project Online applications are a Project Online account and test data--projects and project-related information that include assignments, tasks, resources, and custom fields. A development environment is needed as well, but specifics of the development environment depend on the type of application and the API interface needed for the application. The next few sections describe development needs for the three API interfaces.
  
The reference documentation describes the object model that is common for all three interfaces, as well as an entity map that shows relations among the object model components.
  
## Project hosted add-in development environment

A hosted add-in is an add-in that resides on the server and is downloaded to a browser for runtime execution. Hosted add-ins can use the JSOM or REST interfaces and are written in JavaScript. Project Online provides references to the JSOM library for runtime execution. Assuming development is on a Windows platform, the needed resources follow:
  
- Visual Studio 2015 (preferred) or Visual Studio 2013
    
- Office development tools for Visual Studio
    
- JavaScript language
    
Visit https://github.com/OfficeDev/Project-JSOM-Copy-Work-Packages for a sample application. 
  
You can download and run the sample in a few easy steps:
  
1. Download and open the sample application
    
2. Update the SiteURL in the Properties window
    
   Project Online examines both the application scope of the add-in and the user permissions to govern access to information on the Project Online host. If access is explicitly denied in either or both settings, Project Online denies access to the information. Otherwise, access is granted.
    
3. Enable sideloading on your site. See the [Configuring Project Online for App Development ](http://nearbaseline.com/2013/12/configuring-project-online-for-app-development/.aspx)article for more information. 
    
4. Build the project.
    
5. Run the project.
    
## Project provider-hosted add-in development environment

Provider hosted add-ins are applications written and residing on any web platform. They can connect and perform data operations using the REST (or CSOM for Microsoft platforms) API. Any language and environment that supports the REST interface can be used for development. 
  
An example of the Windows development environment for this type of application includes the following items:
  
-  Visual Studio 2015 (preferred) or Visual Studio 2013 
    
- Microsoft Office Development Tools for Visual Studio (supplied with Visual Studio 2015 Professional and Enterprise editions)
    
- .NET Framework 4.0 or newer
    
- [SharePointOnline CSOM package](https://www.nuget.org/packages/Microsoft.SharePointOnline.CSOM/.aspx) (for CSOM calls) 
    
- A programming language, such as C# 
    
Visit https://github.com/OfficeDev/Project-Add-in-REST-BasicDataOperations for working sample scripts. 
  
You can run the sample in a few steps:
  
1. Download and open the sample application
    
2. Update the SiteURL in the Properties window
    
   Project Online examines both the application scope of the add-in and the user permissions to govern access to information on the Project Online host. If access is explicitly denied in either or both settings, Project Online denies access to the information. Otherwise, access is granted.
    
3. Enable sideloading on your site. See the [Configuring Project Online for App Development ](http://nearbaseline.com/2013/12/configuring-project-online-for-app-development/.aspx)article for more information. 
    
4. Build the project.
    
5. Run the project.
    
## External/standalone application development environment

A standalone application can call Project Online using the Client Side Object Model (CSOM) or REST to communicate with Project Online to create, retrieve, update, and delete information residing on the server. This is a standalone client application that depends on the user access level to run. 
  
An example of the Windows development environment for this type of application includes the following items:
  
- Visual Studio 2015 (preferred) or Visual Studio 2013 
    
- Microsoft Office Development Tools for Visual Studio (supplied with Visual Studio 2015 Professional and Enterprise editions)
    
- .NET Framework 4.0 or newer
    
- [SharePointOnline CSOM package](https://www.nuget.org/packages/Microsoft.SharePointOnline.CSOM/.aspx) (for CSOM calls) 
    
- A programming language, such as C# 
    
Visit https://github.com/OfficeDev/Project-CSOM-Read-Enterprise-CustomFields for a sample application. 
  
You can run the sample in a few steps:
  
1. Download the sample application
    
2. Make a couple of changes to access your Project Online site—the site name, user account, and password.
    
   Ensure the user has access to all projects. Project Online uses user permissions to govern access to information in the data store.
    
3. Add the SharePoint assembly to the references using the Nuget Package Manager Console, available from the Tools menu by typing the following in the Nuget console: 
    
   `Install-Package Microsoft.SharePointOnline.CSOM`

4. Build the project.
    
5. Run the project.
    
## Next steps

Each sample application has an article to explain the highlights of working with the individual Project API. The articles appear in the following list, along with a few articles that describe the entity relationships, information on the query system, and accessing Custom Fields. 
  
- [Developing a Project Online Application Using the Client-side Object Model](developing-a-project-online-application-using-the-client-side-object-model.md)
    
- [Developing a Project Online add-in using the JavaScript Object Model (JSOM)](developing-a-project-online-add-in-using-the-javascript-object-model-jsom.md)
    
- [Accessing Project Online enterprise custom fields](accessing-project-online-enterprise-custom-fields.md)
    
## See also

For documentation and samples related to Project Online and application development using CSOM, see the [Project Development Portal](http://dev.office.com/project.aspx).
    

