---
title: "EntityType Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 420d7b7b-507b-4a3e-8e50-f2454ec1e08d
description: "Contains the properties that define the reporting data for a project in the ProjectData service."
---

# EntityType: Project (ProjectData service)

Contains the properties that define the reporting data for a project in the **ProjectData** service. 
  
## Example

The following REST query uses the [Projects](entityset-projects-projectdata-service.md) entity set and the **ProjectId** key to get the start and finish dates for a specified project. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/Projects
    ?$select=ProjectStartDate,ProjectFinishDate
    &amp;$filter=ProjectId eq guid'7e910f5b-95e2-e111-8d29-00155d35d32e'
```

The following REST query uses the **Tasks** entity set and the **ProjectId** key to get the tasks in a specified project. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/Tasks
    ?$filter=ProjectId eq guid'7e910f5b-95e2-e111-8d29-00155d35d32e'
```

The following statement uses LINQ query syntax to retrieve **Project** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Projects** entity set can then be accessed as  `context.Projects`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from p in Projects
    where p.ProjectStartDate > new DateTime(2012, 1, 1)
    orderby p.ProjectName
    select new
    {
        Project = p.ProjectName,
        StartDate = p.ProjectStartDate,
        FinishDate = p.ProjectFinishDate,
        ProjectCost = p.ProjectCost
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Projects
    .Where(p => (p.ProjectStartDate > (DateTime?)(new DateTime(2012, 1, 1))))
    .OrderBy(p => p.ProjectName)
    .Select(p => new
    {
        Project = p.ProjectName,
        StartDate = p.ProjectStartDate,
        FinishDate = p.ProjectFinishDate,
        ProjectCost = p.ProjectCost
    });
```

Either statement creates the following REST URL (all on one line).
  
```
http://<pwa_url>/_api/ProjectData/Projects?
    $filter=ProjectStartDate gt datetime'2012-01-01T00:00:00'&amp;
    $orderby=ProjectName&amp;
    $select=ProjectName,ProjectStartDate,ProjectFinishDate,ProjectCost
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**StartDate**|**FinishDate**|**ProjectCost**|
|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |3/1/2012 8:00:00 AM  <br/> |3/15/2012 5:00:00 PM  <br/> |$1124.00  <br/> |
|ProjectB  <br/> |3/1/2012 8:00:00 AM  <br/> |3/24/2012 5:00:00 PM  <br/> |$2171.00  <br/> |
|ProjectC  <br/> |3/1/2012 8:00:00 AM  <br/> |3/17/2012 5:00:00 PM  <br/> |$1968.00  <br/> |
   
## Definition

```XML
<EntityType Name="Project">
  <Key>
    <PropertyRef Name="ProjectId" />
  </Key>
  <Property Name="EnterpriseProjectTypeDescription" Type="Edm.String" />
  . . .
  <NavigationProperty Name="Tasks" Relationship="ReportingData.Project_Tasks_Task_Project" 
                      ToRole="Task_Project" FromRole="Project_Tasks" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a project and navigation properties of that project. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and assignments, that are associated with a project. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** element specifies the property that is the primary key for a project query. **ProjectId** is the project GUID. 
  
### Property elements

The following table lists the **Property** elements for the **Project** entity. The **Name**, **Type**, and **Nullable** columns are attribute values for each property. 
  
**Attributes values for the Property elements of Project**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**EnterpriseProjectTypeDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of an enterprise project type ( **EPT**).  <br/> |
|**EnterpriseProjectTypeId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of an enterprise project type.  <br/> |
|**EnterpriseProjectTypeIsDefault** <br/> |**Edm.Boolean** <br/> |**true** <br/> |Specifies whether an enterprise project type is the default.  <br/> |
|**EnterpriseProjectTypeName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of an enterprise project type.  <br/> |
|**OptimizerCommitDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The commit date and time of an Optimizer solution in an analysis.  <br/> |
|**OptimizerDecisionAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of an Optimizer decision alias lookup table.  <br/> |
|**OptimizerDecisionAliasLookupTableValueId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of an Optimizer decision alias lookup table value.  <br/> |
|**OptimizerDecisionID** <br/> |**Edm.Byte** <br/> |**true** <br/> |The GUID of an Optimizer decision.  <br/> |
|**OptimizerDecisionName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of an Optimizer decision.  <br/> |
|**OptimizerSolutionName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of an Optimizer solution.  <br/> |
|**ParentProjectId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a parent project.  <br/> |
|**PlannerCommitDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The commit date and time for a project in the project portfolio planner.  <br/> |
|**PlannerDecisionAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a project portfolio planner lookup table that stores the forced-in/forced-out value.  <br/> |
|**PlannerDecisionAliasLookupTableValueId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a value in a project portfolio planner lookup table that stores the forced-in/forced-out value.  <br/> |
|**PlannerDecisionID** <br/> |**Edm.Byte** <br/> |**true** <br/> |The GUID of a project portfolio planner result.  <br/> |
|**PlannerDecisionName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project portfolio planner result.  <br/> |
|**PlannerEndDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The project portfolio planner end date and time.  <br/> |
|**PlannerSolutionName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project portfolio planner solution.  <br/> |
|**PlannerStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The project portfolio planner start date and time.  <br/> |
|**ProjectActualCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for work that has already been performed on a project.  <br/> |
|**ProjectActualDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual length of a project.  <br/> |
|**ProjectActualFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date that a project was complete.  <br/> |
|**ProjectActualOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost incurred for overtime work that has already been performed on a project.  <br/> |
|**ProjectActualOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The overtime work that has already been performed on a project.  <br/> |
|**ProjectActualRegularCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost incurred for regular, nonovertime work that has already been performed on a project.  <br/> |
|**ProjectActualRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The regular, nonovertime work that has already been performed on a project.  <br/> |
|**ProjectActualStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The project actual start date and time.  <br/> |
|**ProjectActualWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The work that has already been performed on a project.  <br/> |
|**ProjectACWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual cost incurred for work that has already been performed on a project, up to the project status date or today's date.  <br/> |
|**ProjectAuthorName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the author of the project.  <br/> |
|**ProjectBCWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work that has already been performed on a project.  <br/> |
|**ProjectBCWS** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work that is scheduled for a project.  <br/> |
|**ProjectBudgetCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The projected cost of a project.  <br/> |
|**ProjectBudgetWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The projected amount of work on a project.  <br/> |
|**ProjectCalculationsAreStale** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if project schedule calculations are not up to date.  <br/> |
|**ProjectCalendarDuration** <br/> |**Edm.Int32** <br/> |**true** <br/> |The total span of active working time for all tasks in a project, based on the project calendar that is specified in the Project Information dialog box.  <br/> |
|**ProjectCategoryName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project category.  <br/> |
|**ProjectCompanyName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the company for a project.  <br/> |
|**ProjectCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total cost for a project.  <br/> |
|**ProjectCostVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between baseline costs and scheduled costs of a project.  <br/> |
|**ProjectCPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project Cost Performance Index—the ratio of earned value (Budgeted Cost of Work Performed) to actual cost.  <br/> |
|**ProjectCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date that a project was created.  <br/> |
|**ProjectCurrency** <br/> |**Edm.String** <br/> |**true** <br/> |The project currency character code.  <br/> |
|**ProjectCV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project cost variance, which is the difference between the budgeted cost of work performed and the actual cost of the project.  <br/> |
|**ProjectCVP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Cost variance, which is the difference between the cost of work performed and the actual cost of scheduled work.  <br/> |
|**ProjectDepartments** <br/> |**Edm.String** <br/> |**true** <br/> |The departments that are included in a project.  <br/> |
|**ProjectDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of a project.  <br/> |
|**ProjectDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The duration of a project.  <br/> |
|**ProjectDurationVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project duration variance.  <br/> |
|**ProjectEAC** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project Estimate at Completion—the expected total cost of a project based on performance up to the status date.  <br/> |
|**ProjectEarlyFinish** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The early finish date and time of a project.  <br/> |
|**ProjectEarlyStart** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The early start date and time of a project.  <br/> |
|**ProjectEarnedValueIsStale** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if earned value fields are out of date.  <br/> |
|**ProjectEnterpriseFeatures** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the project is an enterprise project.  <br/> |
|**ProjectFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The scheduled finish date and time of a project.  <br/> |
|**ProjectFinishVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The variance at the completion of a project.  <br/> |
|**ProjectFixedCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The fixed cost of a project.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project.  <br/> |
|**ProjectKeywords** <br/> |**Edm.String** <br/> |**true** <br/> |The keywords for a project.  <br/> |
|**ProjectLateFinish** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The late finish date and time of a project.  <br/> |
|**ProjectLateStart** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The late start date and time of a project.  <br/> |
|**ProjectManagerName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project manager.  <br/> |
|**ProjectModifiedDate** <br/> |**Edm.Datetime** <br/> |**false** <br/> |The date and time that a project was last modified.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**ProjectOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project overtime cost.  <br/> |
|**ProjectOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project overtime work.  <br/> |
|**ProjectOwnerId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of a project owner.  <br/> |
|**ProjectOwnerName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project owner.  <br/> |
|**ProjectPercentCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The percent of a project that is complete.  <br/> |
|**ProjectPercentWorkCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The percent of project work that is complete.  <br/> |
|**ProjectWorkspaceInternalUrl** <br/> |**Edm.String** <br/> |**true** <br/> |The URL of the project site.  <br/> |
|**ProjectRegularCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The regular, nonovertime cost of a project.  <br/> |
|**ProjectRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of regular, nonovertime work in a project.  <br/> |
|**ProjectRemainingCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The remaining cost in a project for work that has not been performed.  <br/> |
|**ProjectRemainingDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of time that remains to complete a project.  <br/> |
|**ProjectRemainingOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The remaining overtime cost of a project.  <br/> |
|**ProjectRemainingOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The remaining overtime work in a project.  <br/> |
|**ProjectRemainingRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining regular, nonovertime cost of a project.  <br/> |
|**ProjectRemainingRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The remaining nonovertime work in a project.  <br/> |
|**ProjectRemainingWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The remaining work in a project.  <br/> |
|**ProjectResourcePlanWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Work involving the allocation of resources on a project.  <br/> |
|**ProjectSPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project schedule performance index.  <br/> |
|**ProjectStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The project start date and time.  <br/> |
|**ProjectStartVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The variance at the start of a project.  <br/> |
|**ProjectStatusDate** <br/> |**Edm.DateTime**.  <br/> |**true** <br/> |The status date and time of a project.  <br/> |
|**ProjectSubject** <br/> |**Edm.String** <br/> |**true** <br/> |The subject of a project.  <br/> |
|**ProjectSV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project schedule variance, which is the difference between earned value (budgeted cost of work performed) and planned value (budgeted cost of work scheduled).  <br/> |
|**ProjectSVP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project Schedule Variance Percentage—schedule variance divided by the project budgeted cost of work scheduled.  <br/> |
|**ProjectTCPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The To-Complete Performance Index. This is an indication of how much work should be performed to meet a project schedule.  <br/> |
|**ProjectTitle** <br/> |**Edm.String** <br/> |**true** <br/> |The title of a project.  <br/> |
|**ProjectType** <br/> |**Edm.Int32** <br/> |**false** <br/> |The enumerated value that represents the type of a project.  <br/> |
|**ProjectVAC** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The project Variance At Completion—the difference between baseline cost and the estimate at completion.  <br/> |
|**ProjectWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The work of a project.  <br/> |
|**ProjectWorkspaceInternalUrl** <br/> |**Edm.String** <br/> |**true** <br/> |The URL of a project site.  <br/> |
|**ProjectWorkVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The work variance of a project.  <br/> |
|**ResourcePlanUtilizationDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The start date and time for use of the resource plan.  <br/> |
|**ResourcePlanUtilizationType** <br/> |**Edm.Int16** <br/> |**true** <br/> |An enumerated value that represents the utilization type of a resource plan.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Project** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute contains two pairs of names; each pair of names indicates the navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Tasks** navigation property, the primary type is **Project**, and the secondary type is **Task**.
  
With the **Project** entity, when navigating from a project to the collection of tasks, the **FromRole** is **Project_Tasks**, and the **ToRole** is **Task_Project**. The roles are reversed for the [EntityType: Task (ProjectData service)](entitytype-task-projectdata-service.md) entity type. 
  
**Attributes of the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**AssignmentBaselines** <br/> |[Project_AssignmentBaselines_AssignmentBaseline_Project](association-element-project_assignmentbaselines-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of assignment baselines and from an assignment baseline to a project.  <br/> |
|**Assignments** <br/> |[Project_Assignments_Assignment_Project](association-project_assignments_assignment_project-projectdata-service.md) <br/> |Establishes navigation from a project to a collection of assignments and from an assignment to a project.  <br/> |
|**Deliverables** <br/> |[Project_Deliverables_Deliverable_Project](association-element-project_deliverables-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of deliverables and from a deliverable to a project.  <br/> |
|**Dependencies** <br/> |[Project_Dependencies_Deliverable_DependentProjects](association-project_dependencies_deliverable_dependentprojects-projectdata-servi.md) <br/> |Establishes navigation from a project to a collection of dependencies and from a deliverable to a dependent project.  <br/> |
|**Issues** <br/> |[Project_Issues_Issue_Project](association-element-project_issues-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of issues and from an issue to a project.  <br/> |
|**Risks** <br/> |[Project_Risks_Risk_Project](association-element-project_risks-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of risks and from a risk to a project.  <br/> |
|**StagesInfo** <br/> |[Project_StagesInfo_ProjectWorkflowStageData_Project](association-project_stagesinfo_projectworkflowstagedata_project-projectdata-serv.md) <br/> |Establishes navigation from a project to a collection of workflow stages and from a workflow stage to a project.  <br/> |
|**Tasks** <br/> |[Project_Tasks_Task_Project](association-project_tasks_task_project-projectdata-service.md) <br/> |Establishes navigation from a project to a collection of tasks and from a task to a project.  <br/> |
   
## See also

#### Reference

[Projects](entityset-projects-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

