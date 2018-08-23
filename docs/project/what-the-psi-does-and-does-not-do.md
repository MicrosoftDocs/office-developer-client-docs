---
title: "What the PSI does and does not do"

 
manager: soliver
ms.date: 09/17/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: eac6be6a-9a20-4bc0-8da2-b2fd93aab04f
description: "The Project Server Interface (PSI) can help to automate many server-side processes in on-premises installations of Project Server 2013. But, several functions require the use of Microsoft Project Professional 2013."
---

# What the PSI does and does not do

The Project Server Interface (PSI) can help to automate many server-side processes in on-premises installations of Project Server 2013. But, several functions require the use of Microsoft Project Professional 2013.
  
|||
|:-----|:-----|
|||
   
The PSI is designed to complement the capabilities of Project Professional 2013, rather than provide a server-based alternative for all Project Professional functions. Third-party developers can use the PSI to help create Web Parts for on-premises installations of Project Web App and project workspaces, create custom Windows applications and web applications that interact with on-premises Project Server data, develop workflow logic for project portfolio management, develop local full-trust event handlers, and integrate Project Server with other applications. The PSI cannot be used for development of apps for the Office Store, mobile devices, or tablets; for that, you can use the client-side object model (CSOM).
  
> [!NOTE]
> The PSI provides a more comprehensive programmatic interface for Project Server 2013 than the CSOM provides. But, unless the CSOM does not provide the functionality that you require, we recommend that you use the CSOM to develop new applications. For more information, see [What the CSOM does and does not do](what-the-csom-does-and-does-not-do.md). 
  
## Usage scenarios for the PSI
<a name="pj14_WhatPSIDoes_UsageScenarios"> </a>

Following are examples of some applications that the PSI supports for server-side projects and calculations:
  
- **Automate the creation or management of entities in Project Server** Although Project Professional 2013 and Project Web App together are designed to handle management and creation of entities such as projects, enterprise resources, and custom fields, there are often cases where a custom application can save time with bulk or repetitive jobs. The PSI can automate several kinds of jobs that the CSOM does not do, for example, with OLAP cubes, project portfolio analyses, business drivers, notifications, object link providers, security, and SharePoint interoperability. 
    
- **Get data in the published or archive tables of the Project database** Because direct database access to the draft, published, and archive tables is not supported, you can use the PSI to read data that is not available in the reporting tables or views. For example, get information about project versions, dates, and changes that are stored in the archive tables, and then populate a JS Grid control in a web part with the information. 
    
- **Validate statusing and timesheet data** Use the PSI in local pre-event handlers to validate assignment status or timesheet data that users enter, before the data is saved in Project Web App. 
    
- **Maintenance projects** Create placeholder projects to use with resource plans. Reserve or book time against resources for maintenance work or base business. Maintenance projects generally do not have tasks. 
    
- **Create financial projects** Create projects for time capture through the timesheet for integration with a financial system. Create a hierarchy of financial codes that reflect the cost breakdown structure of the financial system. Financial projects do not require scheduling or status updates. 
    
- **Integrate with accounting systems** Capture the resource costs and expenses associated with projects to feed financial and billing systems and for budget comparison purposes. Synchronize tasks, resources, and assignments between the systems. Capture timesheet data in one system to feed the other (which timesheet is used depends on the needs of the organization or of individual projects). 
    
- **Automate updates from team members** For projects that are not actively managed, automatically update projects on the server with progress and other changes from project team members. Projects can be updated and republished without a project manager reviewing the results or making adjustments to the plan. 
    
- **Evaluate Project Server data in local full-trust event handlers** A local event handler for the **ProjectCreating** pre-event can use Project Server data from the PSI to help determine whether to cancel an event. For example, before creating a project, compare the project proposal with existing projects. 
    
- **Create custom workflow activities for demand management** Use the PSI in local, full-trust workflow activities to modify and update project proposals based on enterprise project templates. Use project custom fields to tag the project with information needed for the initiation and approval process. Add tasks to identify project phases for key milestones or deliverables. When project proposals are approved, a workflow can change the proposals into full-scale projects that are managed with Project Professional. 
    
- **Create PSI extensions** (**Deprecated.** Extensions are deprecated in Project Server 2013, and will not be supported in future releases.) The PSI can be extended with custom services by using the Windows Communication Foundation (WCF) interface. PSI extensions run on the Project Server computer, and can use the same security infrastructure that the built-in PSI services use. Extensions can query the reporting tables, use separate database tables, consolidate PSI calls to save bandwidth, and integrate with third-party applications and other server-side components. For more information, see [Developing PSI Extensions](http://msdn.microsoft.com/library/1b484623-94fb-47c9-84c1-3e68a9133042%28Office.15%29.aspx).
    
- **Use impersonation in local, full-trust applications** Calls to the WCF interface of the PSI can be impersonated, so that an application assumes the security permissions of the impersonated user. Impersonation should be used sparingly and carefully. Reading and updating status information for other users does not require impersonation. New applications that require impersonation should use the CSOM and the OAuth protocol instead of the PSI. For more information about impersonation with the PSI, see [Use Impersonation with WCF](http://msdn.microsoft.com/library/e3597901-2f02-44a2-8076-d32aae540b38%28Office.15%29.aspx).
    
> [!NOTE]
> In some cases, the PSI can be used in client applications with the CSOM and Project Online. If you use an ASMX-based PSI web service, the application must include a method to authenticate the [Microsoft.ProjectServer.Client.ProjectContext](https://msdn.microsoft.com/library/Microsoft.ProjectServer.Client.ProjectContext.aspx) object in the CSOM and a method to authenticate the **System.Web.Services.Protocols.SoapHttpClientProtocol** client object. For an example that uses a web service with the SharePoint CSOM, see [Remote Authentication in SharePoint Online Using Claims-Based Authentication](http://msdn.microsoft.com/library/49067f7a-3020-478f-ba97-4b7ce3ea9b87%28Office.15%29.aspx). > Because of constrained app-level permissions, the PSI cannot be used in apps that are designed for distribution in the public Office Store. In that case, you can use only the CSOM. 
  
## What the PSI does not do
<a name="pj14_WhatPSIDoes_DoesNotDo"> </a>

Although there are many things the PSI can do, there are some things the PSI does not do. Following are two things the PSI cannot do, but the CSOM can do.
  
### Project Online and remote event receivers

The primary limitation of the PSI is with Project Online. Applications that use the PSI require full-trust access to an on-premises installation of Project Server. For example, the PSI cannot be used in remote event receivers, where the event receiver is installed as a service on Microsoft Azure.
  
### Workflows and claims authentication

A workflow definition that uses Windows Workflow Foundation version 4 (WF4) requires claims authentication, which the PSI does not directly support. This means you cannot use the PSI to create a project in Project Server 2013 that has an enterprise project type (EPT) with a WF4 workflow definition.
  
You can use the PSI to create projects with EPTs that either have no workflow or use a legacy WF3.5 definition (the workflow version in Project Server 2010). To create a project with an EPT that has a WF4 definition, use the CSOM.
  
 **Actions that require Project Professional:**
  
The following list are things that neither the PSI nor the CSOM can do.
  
#### Local data

- Manipulating data in local projects (.mpp files). For example, defining cost rate tables or availability contours for local resources. 
    
- Defining or editing local base calendars or resource calendars, including calendar exceptions.
    
- Defining local custom fields. (The PSI does support editing local custom field values on tasks, resources, and assignments.)
    
#### Enterprise data

- Checking out or editing the enterprise global template. The enterprise global data in Project Server 2013 is a set of binary data tables in the Project database, not a project template as in Office Project Server 2007 and earlier versions.
    
- Defining or editing enterprise calendars. The [Calendar](https://msdn.microsoft.com/library/WebSvcCalendar.Calendar.aspx) methods manage only calendar exceptions. 
    
#### Master projects and cross-project links

- Creating master projects and inserting subprojects.
    
- Scheduling a critical path across a master project. 
    
- Creating cross-project links.
    
#### Resources

- Requesting or performing resource leveling.
    
- Changing the resource on an assignment. (You can use the PSI to delete the assignment and create a new one.)
    
- Deleting or replacing a resource that has actual work accepted (actuals).
    
- Changing a resource type between work, material, and cost.
    
- Creating or editing resource calendars.
    
- When adding a resource to a task, the PSI does not automatically redistribute work the way Project Professional does. It is up to the developer to choose and explicitly set the work distribution on the assignments.
    
#### Cost resources

- Editing, creating, or deleting cost resources and assignments using the [Project](https://msdn.microsoft.com/library/WebSvcProject.Project.aspx) methods. The [Resource](https://msdn.microsoft.com/library/WebSvcResource.Resource.aspx) methods can create cost resources but cannot edit them. 
    
#### Work contours

- Editing timephased data.
    
    > [!NOTE]
    > The [UpdateStatus](https://msdn.microsoft.com/library/WebSvcStatusing.Statusing.UpdateStatus.aspx) method in the **Statusing** Web service can edit timephased actuals on assignments after the project manager updates and publishes the assignment data. 
  
- Setting or changing the assignment contour type (such as flat, back-loaded, or front-loaded).
    
#### Baselines and earned value

- Saving a baseline or editing baseline data. 
    
- Setting a progress date.
    
- Calculating variance and earned value. 
    
#### Interactive scheduling

- Supporting interactive scheduling. (Because Project Server handles interactions asynchronously, interactive scheduling should be done with Project Professional.)
    
    > [!NOTE]
    > To avoid changing programmatic behavior, the PSI methods that are brought forward from Project Server 2010 act the same way in Project Server 2013. For example, [QueueUpdateProject](https://msdn.microsoft.com/library/WebSvcProject.Project.QueueUpdateProject.aspx) still has the same limitations and uses the older server-side scheduling engine. The new [QueueUpdateProject2](https://msdn.microsoft.com/library/WebSvcProject.Project.QueueUpdateProject2.aspx) method removes many of those limitations and uses the new Project Server 2013 server-side scheduling engine, which is the same scheduling engine that is in Project Professional 2013. 
  
#### WBS

- Defining a work breakdown structure (WBS) code mask. 
    
#### Tasks

- Changing the task type (fixed work, duration, or units).
    
- Changing whether a task is effort-driven.
    
- Changing task fixed-cost accrual.
    
- Changing the content of the [TASK_NOTES](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_NOTES.aspx) field. The PSI can read only the text part of the task notes, which are .rtf binary data. But, you can edit assignment notes ( [ASSN_NOTES](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.AssignmentRow.ASSN_NOTES.aspx) ), which are text data. The Reporting database does not include task or assignment notes. 
    
- Creating or editing recurring tasks.
    
- Assigning or changing the task calendar on existing tasks.
    
- Creating a new task with a task calendar.
    
- Changing the value of the [TASK_IGNORES_RES_CAL](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_IGNORES_RES_CAL.aspx) field (task ignores resource calendar). 
    
- Changing the active status of a task by using [QueueUpdateProject](https://msdn.microsoft.com/library/WebSvcProject.Project.QueueUpdateProject.aspx) , if additional changes are made in the same call. For more information, see the  *Project Scheduling on the Server*  section in [Project Server programmability](project-server-programmability.md).
    
#### Summary tasks

- Creating or changing assignments on summary tasks.
    
    > [!NOTE]
    > We recommend that you do not make assignments on summary tasks using Project Professional or any other way. For more information, see the  *Project Scheduling on the Server*  section in [Project Server programmability](project-server-programmability.md). 
  
- Editing summary task fields that are normally rolled up from the subtask. Server-side projects always roll up summary information, instead of setting information on the summary task and pushing it down to the subtasks. You can edit only the following fields on summary tasks:
    
  - Task dependencies
    
  - Non-formula custom fields
    
  - [TASK_NAME](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_NAME.aspx)
    
  - [TASK_OUTLINE_LEVEL](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_OUTLINE_LEVEL.aspx)
    
  - [TASK_IS_MARKED](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_IS_MARKED.aspx)
    
  - [TASK_CONSTRAINT_TYPE](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_CONSTRAINT_TYPE.aspx)
    
  - [TASK_CONSTRAINT_DATE](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_CONSTRAINT_DATE.aspx)
    
  - [TASK_PRIORITY](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_PRIORITY.aspx)
    
  - [TASK_DEADLINE](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_DEADLINE.aspx)
    
  - [TASK_FIXED_COST](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_FIXED_COST.aspx)
    
  - [TASK_FIXED_COST_ACCRUAL](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_FIXED_COST_ACCRUAL.aspx) (set the value only when creating the task) 
    
  - [TASK_WBS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.TaskRow.TASK_WBS.aspx)
    
For the project summary task, the PSI limitations are the same as for Project Professional. The PSI can edit budget assignments—including cost budgets.
  
#### Project-level calculation options

- Changing a project type between Schedule From Start (SFS) and Schedule From Finish (SFF). (The PSI can create a project as either SFS or SFF, but once created it can be changed only in Project Professional.)
    
- Changing the project base calendar ([CAL_UID](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.CAL_UID.aspx) ) after project creation. 
    
- Changing options for calculations. You can use the PSI to set the following calculation options when the project is created, but changing the options requires Project Professional. (In Backstage view, choose **Options**, and then choose the **Schedule** tab in the **Project Options** dialog box.) 
    
  - [PROJ_OPT_CALC_ACT_COSTS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_CALC_ACT_COSTS.aspx)
    
  - [PROJ_OPT_CRITICAL_SLACK_LIMIT](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_CRITICAL_SLACK_LIMIT.aspx)
    
  - [PROJ_OPT_HONOR_CONSTRAINTS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_HONOR_CONSTRAINTS.aspx)
    
  - [PROJ_OPT_MOVE_ACTUAL_IF_LATER](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_MOVE_ACTUAL_IF_LATER.aspx)
    
  - [PROJ_OPT_MOVE_ACTUAL_TO_STATUS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_MOVE_ACTUAL_TO_STATUS.aspx)
    
  - [PROJ_OPT_MOVE_REMAINING_IF_EARLIER](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_MOVE_REMAINING_IF_EARLIER.aspx)
    
  - [PROJ_OPT_MOVE_REMAINING_TO_STATUS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_MOVE_REMAINING_TO_STATUS.aspx)
    
  - [PROJ_OPT_MULT_CRITICAL_PATHS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_MULT_CRITICAL_PATHS.aspx)
    
  - [PROJ_OPT_SPLIT_IN_PROGRESS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_SPLIT_IN_PROGRESS.aspx)
    
  - [PROJ_OPT_SPREAD_ACT_COSTS](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_SPREAD_ACT_COSTS.aspx)
    
  - [PROJ_OPT_SPREAD_PCT_COMP](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_SPREAD_PCT_COMP.aspx)
    
  - [PROJ_OPT_TASK_UPDATES_RES](https://msdn.microsoft.com/library/WebSvcProject.ProjectDataSet.ProjectRow.PROJ_OPT_TASK_UPDATES_RES.aspx)
    
## See also

- [What the CSOM does and does not do](what-the-csom-does-and-does-not-do.md)  
- [Project Server programmability](project-server-programmability.md)   
- [Remote Authentication in SharePoint Online Using Claims-Based Authentication](http://msdn.microsoft.com/library/49067f7a-3020-478f-ba97-4b7ce3ea9b87%28Office.15%29.aspx)  
- [Office Add-ins](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins) 
    

