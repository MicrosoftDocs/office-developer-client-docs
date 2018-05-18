---
title: "ProjectData - Project OData service reference"

 
manager: soliver
ms.date: 8/10/2016
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 1ed14ee9-1a1a-4960-9b66-c24ef92cdf6b
description: "ProjectData is a WCF Data Service, also known as an OData service. The ProjectData service is implemented with the OData V3 libraries."
---

# ProjectData - Project OData service reference

 **ProjectData** is a WCF Data Service, also known as an OData service. The **ProjectData** service is implemented with the OData V3 libraries. 
  
The **ProjectData** service enables REST queries and a variety of OData client libraries to make both online and on-premises queries of reporting data from a Project Web App instance. For example, you can directly use a REST query in web browsers, or use JavaScript to build web apps and client apps for mobile devices, tablets, PCs, and Mac computers. Client libraries are available for JavaScript, the Microsoft .NET Framework, Microsoft Silverlight, Windows Phone 8, and other languages and environments. In Project Server 2013, the **ProjectData** service is optimized to create pivot tables, pivot charts, and PowerView reports for business intelligence by using the Excel 2013 desktop client and Excel Services in SharePoint. For more information, see [Use Excel 2013 to create a new Project Online report](http://office.microsoft.com/en-us/project-server-help/use-excel-2013-to-create-a-new-project-web-app-report-HA102923779.aspx) and [Server Reporting in PWA](http://blogs.office.com/b/project/archive/2012/10/31/reporting-project-server-pwa-odata.aspx).
  
When Project Server 2013 or Project Online is in Project permission mode, you can explicitly grant or deny access to the OData feed for specified Project Web App users. For example, on the Edit User page in Project Web App, expand the **Global Permissions** section, and then in the **General** section, select the **Access Project Server Reporting Service** check box in the **Allow** column. 
  
> [!NOTE]
> When Project Server is in the default SharePoint permission mode, the **Security Categories** section and **Global Permissions** section are not available on the Edit User page. 
  
In the default SharePoint permission mode, not all Project Web App users have access to the OData feed. Only users in the following groups have access: Portfolio Viewers, Portfolio Managers, and Administrators. Access cannot be managed for individual entities in the OData feed; that is, if a user has access to the OData service, she can get reporting data that is published for all of the projects, resources, tasks, and other entities. For more information about the permission modes, see [Plan user access in Project Server 2013](http://technet.microsoft.com/en-us/library/fp161361%28v=office.15%29.aspx).
  
You can access the **ProjectData** service through a Project Web App URL. The XML structure of the EDM is available from the  `http://<pwa_site>/_api/ProjectData/$metadata` endpoint (example:  `http://contoso.com/sites/pwa/_api/ProjectData/$metadata`). To view a feed that contains the collection of projects, for example, you can use the following REST query in a browser:  `http://<pwa_site>/_api/ProjectData/Projects`. When you view the webpage source in the browser, you see the XML data for each project, with properties of the **Project** entity type that the **ProjectData** service exposes. 
  
The EDM of the **ProjectData** service is an XML document that conforms to the OData specification. The EDM shows the entities that are available in the reporting data and the associations between entities. The EDM includes the following two **Schema** elements: 
  
- The **Schema** element for the **ReportingData** namespace defines **EntityType** elements and **Association** elements: 
    
  - **EntityType elements:** Each entity type, such as **Project** and **Task**, specifies the set of properties, including navigation properties, that are available for that entity. For example, task properties include the task name, task GUID, and project name for that task. Navigation properties define how a query for an entity such as **Project** is able to navigate to other entities or collections, such as **Tasks** within a project. Navigation properties define the start role and end role, where roles are defined in an **Association** element. 
    
  - **Association elements:** An association relates one entity to another by endpoints. For example, in the **Project_Tasks_Task_Project** association, **Project_Tasks** is one endpoint that relates a **Project** entity to the tasks within that project. **Task_Project** is the other endpoint, which relates a **Task** entity to the project in which the task resides. 
    
- The **Schema** element for the **Microsoft.Office.Project.Server** namespace includes just one **EntityContainer** element, which contains the child elements for entity sets and association sets. The **EntitySet** element for **Projects** represents all of the projects in a Project Web App instance; a query of **Projects** can get the collection of projects that satisfy a filter or other options in a query. 
    
    An **AssociationSet** element is a collection of associations that define the primary keys and foreign keys for relationships between entity collections. Although the  `~/_api/ProjectData/$metadata` query results include the **AssociationSet** elements, they are used internally by the OData implementation for the **ProjectData** service, and are not documented. 
    
 **Limits for ProjectData queries**
  
There are limits to the number of entities that can be returned in one query of the **ProjectData** service. The following table shows the default per-query limits for on-premises and online instances. 
  
> [!NOTE]
> The Project Online infrastructure supports higher limits for many entity sets. You shouldn't attempt to apply them to an on-premises instance. 
  
|**Entity set**|**On-premises**|**Online**|
|:-----|:-----|:-----|
|AssignmentBaselines  <br/> |100  <br/> |300  <br/> |
|AssignmentBaselineTimephasedDataSet  <br/> |200  <br/> |2000  <br/> |
|Assignments  <br/> |100  <br/> |1000  <br/> |
|AssignmentTimephasedDataSet  <br/> |100  <br/> |2000  <br/> |
|BusinessDriverDepartments  <br/> |200  <br/> |200  <br/> |
|BusinessDrivers  <br/> |200  <br/> |200  <br/> |
|CostConstraintScenarios  <br/> |200  <br/> |1000  <br/> |
|CostScenarioProjects  <br/> |200  <br/> |2000  <br/> |
|Deliverables  <br/> |200  <br/> |1000  <br/> |
|EngagementsTimephasedDataSet  <br/> ||200  <br/> |
|Issues  <br/> |200  <br/> |1000  <br/> |
|IssueTaskAssociations  <br/> |100  <br/> |2000  <br/> |
|PortfolioAnalyses  <br/> |200  <br/> |200  <br/> |
|PortfolioAnalysisProjects  <br/> |200  <br/> |2000  <br/> |
|PrioritizationDriverRelations  <br/> |200  <br/> |1000  <br/> |
|PrioritizationDrivers  <br/> |200  <br/> |1000  <br/> |
|Prioritizations  <br/> |200  <br/> |200  <br/> |
|ProjectBaselines  <br/> |200  <br/> |200  <br/> |
|Projects  <br/> |100  <br/> |300  <br/> |
|ProjectWorkflowStageDataSet  <br/> |200  <br/> |2000  <br/> |
|ResourceConstraintScenarios  <br/> |200  <br/> |1000  <br/> |
|Resources  <br/> |100  <br/> |1000  <br/> |
|ResourceScenarioProjects  <br/> |200  <br/> |2000  <br/> |
|ResourceTimephasedDataSet  <br/> |200  <br/> |2000  <br/> |
|Risks  <br/> |200  <br/> |1000  <br/> |
|RiskTaskAssociations  <br/> |100  <br/> |2000  <br/> |
|TaskBaselines  <br/> |100  <br/> |300  <br/> |
|TaskBaselineTimephasedDataSet  <br/> |200  <br/> |2000  <br/> |
|Tasks  <br/> |100  <br/> |300  <br/> |
|TaskTimephasedDataSet  <br/> |100  <br/> |2000  <br/> |
|TimeSet  <br/> |100  <br/> |2000  <br/> |
|TimesheetClasses  <br/> |200  <br/> |1000  <br/> |
|TimesheetLineActualDataSet  <br/> |100  <br/> |2000  <br/> |
|TimesheetLines  <br/> |100  <br/> |1000  <br/> |
|TimesheetPeriods  <br/> |200  <br/> |1000  <br/> |
|Timesheets  <br/> |100  <br/> |1000  <br/> |
   
For on-premises instances of Project Server, you can use the [Get-SPProjectOdataConfiguration](http://technet.microsoft.com/en-us/library/jj219516%28v=office.15%29.aspx) command in Windows PowerShell to get the query limits for entities in the **ProjectData** service. For example, on the Project Server computer, run **SharePoint 2013 Management Shell** as an administrator, and then run the following command. Results are shown below the command. 
  
```powershell
(Get-SPProjectOdataConfiguration).EntitySetsWithMaxPAgeSizeOverride
Key                                                                       Value
---                                                                       -----
AssignmentBaselineTimephasedDataSet                                         200
ProjectBaselines                                                            200
ResourceTimephasedDataSet                                                   200
TaskBaselineTimephasedDataSet                                               200
BusinessDrivers                                                             200
BusinessDriverDepartments                                                   200
Prioritizations                                                             200
PrioritizationDrivers                                                       200
PrioritizationDriverRelations                                               200
PortfolioAnalyses                                                           200
PortfolioAnalysisProjects                                                   200
CostConstraintScenarios                                                     200
ResourceConstraintScenarios                                                 200
CostScenarioProjects                                                        200
ResourceScenarioProjects                                                    200
Issues                                                                      200
Risks                                                                       200
Deliverables                                                                200
TimeSet                                                                     200
ProjectWorkflowStageDataSet                                                 200
TimesheetClasses                                                            200
TimesheetPeriods                                                            200
```

For on-premises instances of Project Server, you can also use the [Set-SPProjectOdataConfiguration](http://technet.microsoft.com/en-us/library/jj219516%28v=office.15%29.aspx) command in Windows PowerShell to override the default query page size for any specified entity set, or override the default page size for all entity sets. For example, run the **SharePoint 2013 Management Shell** as an administrator, and then run the following command: 
  
> [!CAUTION]
> Although you can change on-premises limits, we recommend that you keep the default values. Changing them could adversely affect server performance. 
  
```powershell
Set-SPProjectOdataConfiguration -EntitySetName Projects -PageSizeOverride 200
```

For a Project Web App instance that contains a large number of entities, such as projects, assignments, or tasks, you should limit the data returned in at least one of the following ways. If you don't limit the data returned, the query can exceed the default limits and affect server performance.
  
- Use a  _$filter_ URL option, or use  _$select_ to limit the data. For example, the following query filters by project start date and returns only four fields, in order of the project name (the query is all on one line): 
    
  ```html
  http://ServerName/ProjectServerName/_api/ProjectData/Projects?
      $filter=ProjectStartDate gt datetime'2012-01-01T00:00:00'&
      $orderby=ProjectName&
      $select=ProjectName,ProjectStartDate,ProjectFinishDate,ProjectCost
  ```

- Get an entity collection by using an association. For example, the following query internally uses the **Project_Assignments_Assignment_Project** association to get all of the assignments in a specific project (all on one line): 
    
  ```html
  http://ServerName/ProjectServerName/_api/ProjectData
      /Projects(guid'263fc8d7-427c-e111-92fc-00155d3ba208')/Assignments
  ```

- Do multiple queries to return data one page at a time, by using the  _$top_ operator and the  _$skip_ operator in a loop. For example, the following query gets issues 11 through 20 for all projects, in order of the resource who is assigned to the issue (all on one line): 
    
  ```html
  http://ServerName/ProjectServerName/_api/ProjectData
      /Issues?$skip=10&$top=10&$orderby=AssignedToResource
  ```

    For more information, see [OData System Query Options Using the REST Endpoint](http://msdn.microsoft.com/en-us/library/gg309461.aspx).
    
For more information about query string options such as  _$filter_,  _$orderby_,  _$skip_, and  _$top_, see also [OData URL conventions](http://www.odata.org/documentation/odata-version-3-0/url-conventions).
  
> [!NOTE]
> The **ProjectData** service does not implement the  _$links_ query option or the  _$expand_ query option. Excel 2013 internally uses the **Association** elements and the **AssociationSet** elements in the entity data model to help create associations between entities, for pivot tables and other constructs. 
  
## Reference

- [Introducing OData](http://msdn.microsoft.com/en-us/data/hh237663)
    
- [OData protocol](http://www.odata.org/documentation/odata-version-3-0/odata-version-3-0-core-protocol)
    
- [OData URL conventions](http://www.odata.org/documentation/odata-version-3-0/url-conventions)
    
## See also

#### Other resources

[Plan user access in Project Server 2013](http://technet.microsoft.com/en-us/library/fp161361%28v=office.15%29.aspx)
  
[OData System Query Options Using the REST Endpoint](http://msdn.microsoft.com/en-us/library/gg309461.aspx)
  
[Set-SPProjectOdataConfiguration](http://technet.microsoft.com/en-us/library/jj219516%28v=office.15%29.aspx)
  
[Use Excel 2013 to create a new Project Online report](http://office.microsoft.com/en-us/project-server-help/use-excel-2013-to-create-a-new-project-web-app-report-HA102923779.aspx)
  
[Server Reporting in PWA](http://blogs.office.com/b/project/archive/2012/10/31/reporting-project-server-pwa-odata.aspx)

