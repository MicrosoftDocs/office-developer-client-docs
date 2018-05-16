---
title: "Project PSI reference overview"

 
manager: soliver
ms.date: 9/17/2015
ms.audience: Developer
 
f1_keywords:
- Admin
- Archive
- Authentication
- Calendar
- CubeAdmin
- CustomFields
- Events
- LoginForms
- LoginWindows
- LookupTable
- Notifications
- ObjectLinkProvider
- Project
- Project Server Interface
- Project Server Web services
- PSI
- PSI reference
- PSI Web services
- PWA
- QueueSystem
- Resource
- ResourcePlan
- Rules
- Security
- Statusing
- StatusReports
- TimeSheet
- Version
- View
- Web service
- Web services
- WinProj
- WssInterop
keywords:
- web service, calendar,Authentication, Web service,ResourcePlan, Web service,StatusReports, Web service,PSI, namespaces,Event handlers, Project Server,Web service, Notifications,QueueSystem, Web service,Project 2013, platform,LoginWindows, Web service,Web service, Statusing,Web service, Resource,WinProj, Web service,WssInterop, Web service,Web service, Winproj,Event handlers,LookupTable, Web service,PWA, Web service,Web service, Security,Notifications, Web service,Web service, TimeSheet,Web service, QueueSystem,PSI, Web services,Web service, Events,PSI, programming,Web service, LookupTable,Version, Web service,CustomFields, Web service,Web service, PWA,PSI,Resource, Web service,Web service, ResourcePlan,TimeSheet, Web service,Web service, Rules,PSI, managed code reference,Security, Web service,Web service, CustomFields,URL, for the PSI,Web service, WssInterop,Web service, Admin,Web reference, PSI,Web service, CubeAdmin,View, Web service,Calendar, Web service,Web service, View,Admin, Web service,LoginForms, Web service,Web service, LoginForms,PSI, URLs,ObjectLinkProvider, Web service,Archive, Web service,CubeAdmin, Web service,Rules, Web service,Web service, Authentication,Web services, PSI,Project Server, events,Events, Web service,Web service, Project,Statusing, Web service,Web service, ObjectLinkProvider,Project Server Interface,Web methods, PSI,Web service, StatusReports,Web service, Archive,Project, Web service,Web service, LoginWindows
 
localization_priority: Normal
ms.assetid: d3c33089-0cbe-48c3-bfc0-0be819ca4d73
description: "The Project Server Interface (PSI) is the API to use for developing applications that integrate with Project Server 2013 on-premises."
---

# Project PSI reference overview

The Project Server Interface (PSI) is the API to use for developing applications that integrate with Project Server 2013 on-premises.
  
This article is an overview of the documented assemblies, namespaces, and services in the PSI. The [Project Server 2013 class library and web service reference](http://msdn.microsoft.com/library/ef1830e0-3c9a-4f98-aa0a-5556c298e7d1%28Office.15%29.aspx) in the SDK contains all of the managed code documentation for the PSI and the [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx) namespace in Project Server 2013. To develop applications for Project Online, you must use the **Microsoft.ProjectServer.Client** namespace instead of the PSI. 
  
## Introduction to the PSI reference
<a name="pj15_PSIRefOverview_Intro"> </a>

The PSI in Project Server 2013 has a dual interface. The ASMX interface for web services is defined by discovery and Web Service Description Language (disco and WSDL) files in the  `http://ServerName/ProjectServerName/_vti_bin/psi/` virtual directory (for example, Projectdisco.aspx and Projectwsdl.aspx). You can access the ASMX interface only through the URL of an on-premises installation of Project Web App (for example,  `http://ServerName/ProjectServerName/_vti_bin/psi/project.asmx?wsdl)`. To show the web service in a browser, you must include the  `?wsdl` URL option. Because the ASMX interface is built using the Windows Communication Foundation (WCF) infrastructure, the .asmx files for Project Server web services do not actually exist in the virtual PSI directory. 
  
The WCF services interface is defined by .svc files in the back-end  `http://ServerName:32843/GUID/PSI/` virtual directory in the SharePoint Web Services application. The URL of PSI services in the Project Service Application virtual directory (for example,  `http://ServerName:32843/GUID/PSI/project.svc`) includes the .svc files. But, you cannot directly use the back-end URL to set a WCF service reference. To develop an application or component that uses the WCF services of the PSI, you can use a proxy assembly or a proxy file. The Project 2013 SDK download includes proxy files for the WCF services in Project Server 2013, and scripts to get updated WCF proxy files and to compile the files into a proxy assembly for more recent Project Server builds.
  
The Project Service Application directory name is a GUID value, which is the same as the GUID of the on-premises Project Web App instance. In the **Internet Information Services (IIS) Manager** window, expand the **SharePoint Web Services** node, choose the GUID directory name, and then choose **Advanced Settings** to copy the **Virtual Path** value. 
  
> [!IMPORTANT]
> The ASMX web service interface of the PSI is deprecated in Project Server 2013, but is still supported. New applications should use the WCF interface of the PSI or the CSOM. For more information about deprecated features, see [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md)> New applications, and middleware components that run only on an on-premises installation of Project Server, should use the WCF interface, which is the technology that we recommend for network communications. Legacy applications that use the ASMX interface must use the URL through Project Web App, which checks Project Server permissions. For more information about the ASMX interface and how to use the WCF interface, see [Prerequisites for ASMX-based code samples in Project](prerequisites-for-asmx-based-code-samples-in-project.md) and [Prerequisites for WCF-based code samples in Project](prerequisites-for-wcf-based-code-samples-in-project.md). 
  
For developing applications that use the WCF interface, you can use Visual Studio 2010 or Visual Studio 2012. For creating declarative Project Server workflows, you can use SharePoint Designer 2013. Project Server workflows that require access to the PSI or the CSOM can be developed with Visual Studio 2012.
  
### Using the PSI reference
<a name="pj15_PSIRefOverview_Using"> </a>

The PSI object model is large, and many classes and members are for internal use only. As a result, it can be confusing to find the topics that you want in the [Project Server 2013 class library and web service reference](http://msdn.microsoft.com/library/ef1830e0-3c9a-4f98-aa0a-5556c298e7d1%28Office.15%29.aspx). Most of the reference topics that you will use for development are in the following groups:
  
- **Primary class methods:** Each service in the PSI includes a primary class that is named for the name of the service. For example, the **Resource** service contains the [Resource](https://msdn.microsoft.com/library/WebSvcResource.Resource.aspx) class, which is in the [WebSvcResource](https://msdn.microsoft.com/library/WebSvcResource.aspx) namespace. To see a list of the methods that are available in the **Resource** class, expand the class node in the content pane, and then choose the **Resource Methods** topic. 
    
- **DataRow properties:** Many of the primary class methods use or return a **DataSet**. Each **DataTable** object in a **DataSet** contains data in one or more **DataRow** objects. In most cases, you need to see only the row properties, not all of the other members of the **DataSet**, **DataTable**, or **DataRow** classes. For example, the **ResourceAssignmentDataSet** class includes subclasses for the **ResourceAssignmentDataTable** and the [ResourceAssignmentDataSet.ResourceAssignmentRow](https://msdn.microsoft.com/library/WebSvcResource.ResourceAssignmentDataSet.ResourceAssignmentRow.aspx) class. To see a list of properties that are in the **ResourceAssignmentRow** class, expand the class node in the content pane, and then choose the **ResourceAssignmentDataSet.ResourceAssignmentRow Properties** topic. 
    
In addition to the service namespaces, the [Project Server 2013 class library and web service reference](http://msdn.microsoft.com/library/ef1830e0-3c9a-4f98-aa0a-5556c298e7d1%28Office.15%29.aspx) topic links to the three Project Server assemblies that are used in development of third-party solutions for on-premises installations. We provide only minimal documentation for these assemblies. The PSI reference documents the main classes and members in the 23 public services. Six PSI services are for internal use only, and are not documented. 
  
> [!NOTE]
> Classes in the client-side object model (CSOM) can be used independently from the other Project Server assemblies and services. You can use the **Microsoft.ProjectServer.Client** namespace in a remote development environment from the Project Server computer, and develop apps that integrate with Project Online or with an on-premises installation of Project Server. But, the CSOM contains a subset of the functionality of the complete PSI. The CSOM enables development of the most common scenarios for Project Server integration. For more information, see [What the CSOM does and does not do](what-the-csom-does-and-does-not-do.md) and [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx) . 
  
For development of most applications that use the PSI, you do not have to develop on a Project Server computer, or set references to Project Server assemblies in the global assembly cache. You can copy the necessary Project Server assemblies to your development computer. Project Server 2013 installs the following assemblies in  _[Program Files]_ `\Microsoft Office Servers\15.0\Bin`: 
  
- Microsoft.Office.Project.Server.Events.Receivers.dll
    
- Microsoft.Office.Project.Server.Library.dll
    
- Microsoft.Office.Project.Server.Workflow.dll
    
Namespaces for the PSI services have arbitrary names created for a PSI proxy assembly, ProjectServerServices.dll, which is generated for the purpose of documentation. In the PSI reference, each service namespace has a placeholder name (such as  _[Project web service]_) and a web reference (such as  `http://ServerName/ProjectServerName/_vti_bin/psi/Project.asmx?wsdl`). 
  
## Project Server assemblies and namespaces
<a name="pj15_PSIRefOverview_Assemblies"> </a>

Many assemblies are installed when you install Project Server; only four of the Project Server assemblies are documented. Third-party developers generally use only a few classes and members in those assemblies. The undocumented Project Server assemblies include namespaces and classes that Project Server uses internally, such as classes for Project Web App, the business entities, and the data access layer (DAL). When you set a reference in Visual Studio to one of the documented Project Server assemblies, you can see all of the namespaces, classes, and members in the Visual Studio Object Browser.
  
> [!NOTE]
> Many members of the documented Project Server namespaces are used only internally and have minimal documentation. 
  
When developing for Project Online, you can use only the CSOM to access Project Server functionality. You do not have access to the PSI services or the other Project Server assemblies.
  
The [Project Server 2013 class library and web service reference](http://msdn.microsoft.com/library/ef1830e0-3c9a-4f98-aa0a-5556c298e7d1%28Office.15%29.aspx) for the PSI includes namespaces from the following four assemblies: 
  
- **Microsoft.Office.Project.Server.Library.dll** This assembly contains one documented namespace and three undocumented namespaces, as follows: 
    
  - The [Microsoft.Office.Project.Server.Library](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Library.aspx) namespace includes many enumerations, and class fields and properties that are frequently used in on-premises applications for Project Server. For example, developers typically use enumerations such as **CustomField.Type**, and the **PSClientError**, **PSErrorInfo**, and **Filter** classes. 
    
    The **Microsoft.Office.Project.Server.Library** namespace also includes the following seven property classes, which include over 3,200 subclasses: 
    
  - **AssignmentProperties**
    
  - **CalendarProperties**
    
  - **ConstraintProperties**
    
  - **LookupTableProperties**
    
  - **ProjectProperties**
    
  - **ResourceProperties**
    
  - **TaskProperties**
    
    The property classes are used internally and are not documented. The property classes are used for serialization between Project Professional 2013 and Project Server. When you work with the **Microsoft.Office.Project.Server.Library** namespace in Visual Studio, the Object Browser shows all of the property classes, which makes it more difficult to find classes that are useful for third-party development. Because third-party developers do not have to use the property classes, the SDK does not document them. 
    
  - **Microsoft.Office.Project.Server.DataServices** The classes and members of this namespace are used internally by the **OData** service in Project Online for access to the reporting tables in the Project database. The **DataServices** classes are not documented. 
    
  - **Microsoft.Office.Project.Server.Administration** The class and members of this namespace are used internally for diagnostic logging, and are not documented. 
    
  - **Microsoft.Office.Project.Server.Base** The classes and members of this namespace are used internally as base classes and are not documented. 
    
  - **Microsoft.Office.Project.Server.Library.FilterSchema** This namespace is used internally to generate filter schemas and is not documented. 
    
- **Microsoft.Office.Project.Server.Workflow.dll** This assembly is used for legacy Project Server 2010 workflows that can still work in Project Server 2013. For creating new workflows, you should use SharePoint Designer 2013, or you can also use Visual Studio 2012 with the [Microsoft.ProjectServer.Client.WorkflowActivities](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.WorkflowActivities.aspx) class. The Microsoft.Office.Project.Server.Workflow.dll assembly includes the following three namespaces: 
    
  - [Microsoft.Office.Project.Server.Workflow](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Workflow.aspx) This namespace includes classes that are used for Project Server workflow activities. Activities include reading, comparing, and updating project properties. Other classes manage workflows and include workflow call-backs when projects are changed. 
    
  - **Microsoft.Office.Project.PWA** This namespace includes an internal proxy for the PSI, for use with Project Web App and with custom workflow activities; it is not documented. 
    
    A custom workflow activity requires a reference to **Microsoft.Office.Project.PWA** to access all of the classes in the PSI services. For example, the **Microsoft.Office.Project.PWA.PSI** class includes the **ProjectWebService** property, which gets a proxy for the [WebSvcProject](https://msdn.microsoft.com/library/WebSvcProject.aspx) namespace. 
    
  - **Microsoft.Office.Project.Server.WebServiceProxy** This namespace includes internal proxy classes for the primary class in each PSI service. By using the elevated permissions of the workflow user, the workflow can call PSI methods through proxy classes. The proxy classes are not documented. 
    
- **Microsoft.Office.Project.Server.Events.Receivers.dll**[Microsoft.Office.Project.Server.Events](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.aspx) is the only namespace in this assembly. It includes event receiver and event argument classes for the PSI services and other internal classes. 
    
    Developers write event handlers that derive from event receiver classes. Most of the primary classes in the PSI services have a corresponding event receiver class. For example, the **ProjectEventReceiver** class contains pre-event and post-event receiver methods that correspond to methods in the **Project** class in the PSI. The **OnCreating** method and the **OnCreated** method are the pre-event and post-event receiver methods for the **QueueCreateProject** method. 
    
    Developers typically use the following event receiver classes: 
    
  - [AdminEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.AdminEventReceiver.aspx)
    
  - [CalendarEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.CalendarEventReceiver.aspx)
    
  - [CubeAdminEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.CubeAdminEventReceiver.aspx)
    
  - [CustomFieldsEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.CustomFieldsEventReceiver.aspx)
    
  - [LookupTableEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.LookupTableEventReceiver.aspx)
    
  - [ProjectEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.ProjectEventReceiver.aspx)
    
  - [OptimizerEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.OptimizerEventReceiver.aspx)
    
  - [ReportingEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.ReportingEventReceiver.aspx)
    
  - [ResourceEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.ResourceEventReceiver.aspx)
    
  - [SecurityEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.SecurityEventReceiver.aspx)
    
  - [StatusingEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.StatusingEventReceiver.aspx)
    
  - [TimesheetEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.TimesheetEventReceiver.aspx)
    
  - [UserDelegationEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.UserDelegationEventReceiver.aspx)
    
  - [WorkflowEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.WorkflowEventReceiver.aspx)
    
  - [WssInteropEventReceiver](https://msdn.microsoft.com/library/Microsoft.Office.Project.Server.Events.WssInteropEventReceiver.aspx)
    
    The **RulesEventReceiver** class and the **StatusReportsEventReceiver** class are used internally in Project Web App. 
    
- **Microsoft.ProjectServer.Client.dll** This assembly contains the CSOM for development with the .NET Framework 4. The assembly is located in  `%ProgramFiles%\Common Files\Microsoft Shared\Web Server Extensions\15\ISAPI\Microsoft.ProjectServer.Client.dll`. Development of apps with the **Microsoft.ProjectServer.Client** namespace is independent of the on-premises Project Server APIs and services, although the apps can work with either an on-premises or online installation of Project Server. For related CSOM assemblies that can be used for Windows Phone 8, Microsoft Silverlight, or JavaScript with web apps, see [Microsoft.ProjectServer.Client](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.aspx) . 
    
- **Microsoft.Office.Project.Server.Schema.dll** The Project 2013 SDK does not document the **Microsoft.Office.Project.Server.Schema** namespace, which is in the  `[Windows]\Microsoft.NET\assembly\GAC_MSIL\Microsoft.Office.Project.Schema\v4.0_15.0.0.0__71e9bce111e9429c\Microsoft.Office.Project.Schema.dll` assembly. The namespace contains the definitions of all **DataSet**, **DataTable**, and **DataRow** classes used in the PSI, plus many other similar classes that Project Server uses internally. The public classes in each PSI service are documented in the specific service reference. For example, the **DriverDataSet.DriverRow** class is documented in the [WebSvcDriver](https://msdn.microsoft.com/library/WebSvcDriver.aspx) namespace. 
    
    > [!NOTE]
    > Applications that use the CSOM, use remote event handlers, or access Project Online do not use the **Microsoft.Office.Project.Server.Schema** namespace. 
  
    In some applications that use full-trust event handlers, where the event handlers are installed on the Project Server computer, it is necessary to set a reference to the Microsoft.Office.Project.Schema.dll assembly. Following are two examples:
    
  - In a full-trust **OnCreated** post-event handler for custom fields, you can use the **e.CustomFieldInformation** event argument with a reference to the **Microsoft.Office.Project.Server.Schema** namespace for the **CustomFieldDataSet** and **CustomFieldsRow** definitions. 
    
  ```cs
  using PSLibrary = Microsoft.Office.Project.Server.Library;
  using Microsoft.Office.Project.Server.Schema;
  . . .
  // Event handler for the OnCreated event of a custom field.
  public override void OnCreated(
      PSLibrary.PSContextInfo contextInfo, 
      CustomFieldsPostEventArgs e)
  {
      // Get information from the event arguments. 
      string userName = contextInfo.UserName.ToString();
      CustomFieldDataSet customFieldDs = e.CustomFieldInformation;
      CustomFieldsRow customFieldRow = customFieldDs.CustomFields.Rows[0];
      string customFieldName = customFieldRow["MD_PROP_NAME"].ToString();
      byte customFieldType = (byte)customFieldRow["MD_PROP_TYPE_ENUM"];
      Guid customFieldUid = (Guid)customFieldRow["MD_PROP_UID"];
      . . .
  }
  ```

  - A custom workflow activity can require a reference to **Microsoft.Office.Project.Server.Schema** for **DataSet** definitions. 
    
## PSI services
<a name="pj15_PSIRefOverview_PSI"> </a>

The PSI is a set of WCF services and identical ASMX web services for Project Server 2013. To use a service in a Visual Studio project, you set a reference to the URL of the  `.svc` file or the  `.asmx?wsdl` service by using an arbitrary name for the nameservice. The wsdl.exe utility or the svcutil.exe utility then generates proxy source code for that namespace, and the compiler creates a proxy service assembly to include in your application. 
  
> [!NOTE]
> The PSI reference includes placeholder nameservice names for the PSI services such as  _[Admin web service]_,  _[Driver web service]_, and  _[Project web service]_. Each PSI nameservice includes a primary class that contains the web methods for that service. For example, if you set a reference to the **Admin** service and name it **WebSvcAdmin**, then in your application the **WebSvcAdmin** nameservice includes the primary **Admin** class that has the web methods **GetServerCurrency**, **ListInstalledLanguages**, **ReadServerVersion**, and so on. See [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md) for a list of deprecated PSI services. 
  
Of the 30 total PSI services, **authentication**, **ExchangeSync**, **OData**, **P12Upgrade**, **psiserviceapp**, **PWA**, **View**, and **WinProj** are for internal use by Project Web App and Project Professional and are not documented. Although you can create proxy files or a proxy assembly that includes the PSI internal services, the internal services are not for third-party use; the PSI reference does not document those services. Figure 1 shows the location of the back-end PSI services in Internet Information Services Manager. 
  
**Figure 1. Locating the PSI services in IIS**

![PSI services in IIS Manager](media/pj15_PSIReference_IIS.gif)
  
The following are all of the classes that contain web methods in the PSI services:
  
1. [Admin](https://msdn.microsoft.com/library/WebSvcAdmin.Admin.aspx) Includes methods that are used in the **Project Server Administration** pages in Project Web App. Defines fiscal years, manages statusing and currency settings, reporting periods, the audit log, and settings for Active Directory. 
    
2. [Archive](https://msdn.microsoft.com/library/WebSvcArchive.Archive.aspx) Includes methods for managing backup and restoration of projects, security categories, custom fields, resources, system settings, views, and the enterprise global project. Reads and updates the archive schedule. Archives all projects or deletes specified archived projects. Saves backup objects to the Archive database tables and restores backed up objects to the Published database tables. 
    
3. **authentication** Includes methods for internal use only by Project Professional and Project Web App. 
    
4. [Calendar](https://msdn.microsoft.com/library/WebSvcCalendar.Calendar.aspx) Manages enterprise calendar exceptions. Checks out and checks in resource calendars. Creates, deletes, lists all, updates, or returns calendar exceptions. 
    
5. [CubeAdmin](https://msdn.microsoft.com/library/WebSvcCubeAdmin.CubeAdmin.aspx) Manages OLAP cube settings. Gets Analysis Server, database status, and list of cubes. Puts a Cube Build Service request on the queue. Reads and updates calculated member definitions and field settings for dimensions and measures in the cube. 
    
6. [CustomFields](https://msdn.microsoft.com/library/WebSvcCustomFields.CustomFields.aspx) Manages enterprise custom fields. Includes the check out and check in methods, and the create, read, update, and delete (CRUD) methods for enterprise custom fields. 
    
7. [Driver](https://msdn.microsoft.com/library/WebSvcDriver.Driver.aspx) Manages portfolio analysis drivers and driver prioritization for project creation and Demand Management. Includes the CRUD methods for project drivers. 
    
8. [Events](https://msdn.microsoft.com/library/WebSvcEvents.Events.aspx) Manages Project Server event handler associations. Includes the CRUD methods for Project Server event handler associations for a specific event, or for all event handler associations. 
    
9. **ExchangeSync** This is an internal Project Server service that handles Exchange Server events. Project Web App uses **ExchangeSync** to synchronize assignments between Project Server and Exchange Server, instead of synchronizing directly with the Outlook client as in Office Project Server 2007. 
    
    Access to the **ExchangeSync** service is available only through the **ProjectServiceApplication** URL. The **ExchangeSync** classes and members are not supported for third-party development. 
    
10. [LoginForms](https://msdn.microsoft.com/library/WebSvcLoginForms.LoginForms.aspx) Provides the **Login** and **Logoff** methods with Forms-based authentication. Access to the **LoginForms** service is available only on a front-end Project Web App site. 
    
11. [LoginWindows](https://msdn.microsoft.com/library/WebSvcLoginWindows.LoginWindows.aspx) Provides the **Login** and **Logoff** methods that are used for Windows authentication with ASMX-based applications for multiple authentication (claims and Forms-based) Project Server 2013 installations. Access to the **LoginWindows** service is available only on a front-end Project Web App site. 
    
    > [!CAUTION]
    > The **LoginWindows** service is not used in WCF-based applications, or for applications that run on Project Server installations that use only claims authentication or **OAuth**; in those cases, the **Login** method always returns **false**. Claims authentication handles integrated Windows authentication. 
  
12. [LookupTable](https://msdn.microsoft.com/library/WebSvcLookupTable.LookupTable.aspx) Manages lookup tables, multilanguage lookup tables, and their corresponding code masks. Checks out, checks in, reads, creates, deletes, and updates. 
    
13. [Notifications](https://msdn.microsoft.com/library/WebSvcNotifications.Notifications.aspx) Manages alerts and reminders. Includes methods that get, set, register, and unregister alert results. 
    
14. [ObjectLinkProvider](https://msdn.microsoft.com/library/WebSvcObjectLinkProvider.ObjectLinkProvider.aspx) Manages web objects and links for documents and list items on SharePoint sites. Creates, deletes, or reads project, project-linked, task, or task-linked web objects. 
    
    > [!NOTE]
    > The **ObjectLinkProvider** service is deprecated in Project Server 2013. For more information, see the  *Deprecated features*  section in [Updates for developers in Project 2013](updates-for-developers-in-project-2013.md). 
  
15. **OData** Provides the internal **OData** interface for the reporting tables and views. Access to the **OData** service is available only through the back-end **ProjectServiceApplication** URL. The private **OData** service in the PSI provides one method, **ODataClient.ProcessOdataMessage**, which Project Server uses internally to process requests for reporting data. The HTTP requests go through the front-end **ProjectData** service. 
    
    For information about the **ProjectData** service and the OData protocol to read reporting data, see [ProjectData - Project OData service reference](projectdataproject-odata-service-reference.md).
    
16. **P12Upgrade** Provides internal methods for the Project Server 2013 installer to upgrade an Office Project Server 2007 installation. Access to the **P12Upgrade** service is available only through the **ProjectServiceApplication** URL. The **P12Upgrade** methods are not supported for third-party development. 
    
17. [PortfolioAnalyses](https://msdn.microsoft.com/library/WebSvcPortfolioAnalyses.PortfolioAnalyses.aspx) Includes the CRUD methods for project dependencies, and for Optimizer, Planner, and Analysis solutions. 
    
18. [Project](https://msdn.microsoft.com/library/WebSvcProject.Project.aspx) Manages projects. Checks out, checks in, creates, deletes, reads, or updates projects in the Project database draft tables or published tables. Puts a message on the queue for publishing. 
    
    Creates or deletes entities within projects (tasks, resources, assignments, and so on). Gets information about or updates the project team or project site address. Gets project status, a list of projects in the draft tables, all summary tasks, tasks that are available for assignment to a specified resource, or all projects where a resource has assignments.
    
    Creates and manages commitments, creates project proposals and projects from SharePoint task lists, and finds project/master project relationships.
    
19. **psiserviceapp** Used internally by Project Online. The **psiserviceapp** classes and members are not supported for third-party development. 
    
20. **PWA** Contains many methods that are optimized for Project Web App, including the methods for task update approval rules and for managing status reports. The **PWA** methods are often specialized and somewhat redundant compared to equivalent methods in other PSI services. **PWA** methods use or return many of the same datasets as the other PSI methods. 
    
    Access to the **PWA** service is available only through the **ProjectServiceApplication** URL. The **PWA** classes and members are not supported for third-party development. 
    
21. [QueueSystem](https://msdn.microsoft.com/library/WebSvcQueueSystem.QueueSystem.aspx) Manages the Project Server queue. Gets job count, job and job group wait time, status of all jobs, specified jobs, jobs owned by the caller, or jobs for specified projects. Manages job correlation and configures the queue. 
    
22. [Resource](https://msdn.microsoft.com/library/WebSvcResource.Resource.aspx) Manages enterprise resources. Checks out, checks in, updates, or creates resources or Project Server users and their authorization settings; finds resources by name or GUID; reads resource or user data and the resource breakdown structure (RBS) and related security information; gets all assignments for a resource; and resets user passwords. The **Resource** class includes CRUD methods for user delegations. 
    
23. [ResourcePlan](https://msdn.microsoft.com/library/WebSvcResourcePlan.ResourcePlan.aspx) Manages resource plans. Checks out, checks in, publishes, and includes the CRUD methods for resource plans. 
    
24. [Security](https://msdn.microsoft.com/library/WebSvcSecurity.Security.aspx) Includes the CRUD methods for security templates, security categories, organizational and global permissions, and group permissions. The **Security** class includes methods for project categories. 
    
25. [Statusing](https://msdn.microsoft.com/library/WebSvcStatusing.Statusing.aspx) Manages status updates and assignments. Applies status updates or approvals, submits status updates, sets summary information for submitted updates, deletes approved status updates or approval history for a specified user, or deletes all status information for a set of projects. Creates, gets, or delegates assignments; sets assignment work duration. Gets new assignments for the current user; gets assignment or task transaction history, the timephased actuals, or the summary task hierarchy. 
    
    Previews or imports timesheet data, or reads a user's working and nonworking schedule. Finds pending status updates, information for submitted updates, or a transaction record of changes in a submitted update. Reads team status.
    
26. [TimeSheet](https://msdn.microsoft.com/library/WebSvcTimeSheet.TimeSheet.aspx) Manages timesheets. Includes the CRUD methods for timesheets, and submits or recalls timesheets. Finds timesheets that are late or pending approval; finds timesheets by date or period. Gets list of timesheet approvers. Preloads timesheet actuals and validates a timesheet line. The **TimeSheet** class includes the **ReadProjectTimesheetLines** method and the **SubmitTimesheetLines** method for reading and submitting timesheets for another resource without requiring impersonation. 
    
27. **View** The **View** service is designed for use only within Project Web App. Methods in the **View** class manage views and view reports and read fields in views. 
    
    Access to the **View** service is available only through the **ProjectServiceApplication** URL. The **View** methods are not supported for third-party development. 
    
28. **WinProj** The **WinProj** service is designed for use only by Project Professional. Third-party developers should not use **WinProj** methods for programming with Project Server. 
    
    Some **WinProj** methods use datasets such as **ProjectRelationsDataSet** and **ResourceDataSet** that the **Project** and **Resource** services also use, but require specific properties and functions in Project Professional. 
    
    Access to the **WinProj** service is available only through the **ProjectServiceApplication** URL. The **WinProj** methods are not supported for third-party development. 
    
29. [Workflow](https://msdn.microsoft.com/library/WebSvcWorkflow.Workflow.aspx) Includes the CRUD methods for enterprise project types and for managing workflow phases and stages. Runs workflows, sets status information, and manages project detail page (PDP) stages in demand-management workflows. To develop Project Server workflows, developers can use SharePoint Designer 2013 for declarative workflows or use the Office Developer Tools for Visual Studio 2012 for development with .NET Framework 4 and the [Microsoft.ProjectServer.Client.WorkflowActivities](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.WorkflowActivities.aspx) class in the CSOM. 
    
30. [WssInterop](https://msdn.microsoft.com/library/WebSvcWssInterop.WssInterop.aspx) Manages project sites. Creates and deletes project sites. Gets information about and updates SharePoint settings and administration sites. Synchronizes and updates the project site memberships and groups. 
    
Each service namespace includes all of the **DataSet** schema and event handler classes that the service uses. For example,  `Calendar.svc` (or  `Calendar.asmx?wsdl` for the ASMX web service) describes the **Calendar** service. If you name the reference **WebSvcCalendar**, the proxy namespace contains the primary **Calendar** class with the methods **CheckInCalendars**, **CheckOutCalendars**, and so on. The **WebSvcCalendar** proxy namespace also includes the **CalendarDataSet** class and all of its subclasses. 
  
Some of the PSI services contain duplicate **DataSet** classes. For example, the **Project** service and the **Statusing** service both include the **ProjectDataSet** class. This is because methods in both the **Project** service and the **Statusing** service include references to the **ProjectDataSet**, and the proxy assemblies that you create when you set references and compile an application include the related datasets. The **Project** service and **Statusing** service can require values for different fields in the **ProjectDataSet.ProjectRow** class. 
  
When you are navigating the namespaces and classes of the PSI reference, for example to see the web methods for the **Project** service, expand the **[Project web service]** namespace in the **Contents** list, and then expand the **Project** class. 
  
## See also
<a name="pj15_PSIRefOverview_AR"> </a>

- [Project Server 2013 architecture](project-server-2013-architecture.md)
    
- [Project Server programmability](project-server-programmability.md)
    
- [What the PSI does and does not do](what-the-psi-does-and-does-not-do.md)
    
- [Prerequisites for ASMX-based code samples in Project](prerequisites-for-asmx-based-code-samples-in-project.md)
    
- [Prerequisites for WCF-based code samples in Project](prerequisites-for-wcf-based-code-samples-in-project.md)
    
- [.NET Framework Developer Center](http://msdn.microsoft.com/en-us/netframework/aa496123.aspx)
    

