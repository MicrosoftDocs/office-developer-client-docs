---
title: "EntityType Task (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f46f0ea5-1ec4-4b22-91ef-8ae1a168ef4e
description: "Contains the properties that define the reporting data for a task in the ProjectData service."
---

# EntityType: Task (ProjectData service)

Contains the properties that define the reporting data for a task in the **ProjectData** service. 
  
## Example

The following REST query uses the [Tasks](entityset-tasks-projectdata-service.md) entity set and the **TaskId** key to get the specified task and properties. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/Tasks
    ?$filter=TaskId eq guid'2f333a57-f817-e211-9d84-00155d346c3f'
    &amp;$select=TaskPercentCompleted,TaskDuration,TaskFinishDate
```

The following statement uses LINQ query syntax to retrieve **Task** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Tasks** entity set can then be accessed as  `context.Tasks`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from t in Tasks
    where (t.TaskIndex > 0)
    orderby t.ProjectName, t.TaskIndex
    select new
    {
        Project = t.ProjectName,
        Task = t.TaskName,
        TaskWork = t.TaskWork,
        TaskCost = t.TaskCost,
        TaskDuration = t.TaskDuration,
        TaskDurationVariance = t.TaskDurationVariance,
        TaskCostVariance = t.TaskCostVariance
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Tasks
    .Where(t => (t.TaskIndex > (Int32)0))
    .OrderBy(t => t.ProjectName)
    .ThenBy(t => t.TaskIndex)
    .Select(t => new
    {
        Project = t.ProjectName,
        Task = t.TaskName,
        TaskWork = t.TaskWork,
        TaskCost = t.TaskCost,
        TaskDuration = t.TaskDuration,
        TaskDurationVariance = t.TaskDurationVariance,
        TaskCostVariance = t.TaskCostVariance
    });
```

Both preceding statements create the following REST URL (all on one line).
  
```
http://<pwa_url>/_api/ProjectData/Tasks
    ?$filter=TaskIndex gt 0
    &amp;$orderby=ProjectName,TaskIndex
    &amp;$select=ProjectName,TaskName,TaskWork,TaskCost,TaskDuration,TaskDurationVariance,TaskCostVariance
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**Task**|**TaskWork**|**TaskCost**|**TaskDuration**|**TaskDurationVariance**|**TaskCostVariance**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |T1  <br/> |24.0 hrs  <br/> |$404.00  <br/> |24.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectA  <br/> |T2  <br/> |8.0 hrs  <br/> |$156.00  <br/> |8.0 hrs  <br/> |-16.0 hrs  <br/> |-$272.00  <br/> |
|ProjectA  <br/> |T3  <br/> |32.0 hrs  <br/> |$564.00  <br/> |32.0 hrs  <br/> |8.0 hrs  <br/> |$136.00  <br/> |
|ProjectB  <br/> |T1  <br/> |48.0 hrs  <br/> |$836.00  <br/> |48.0 hrs  <br/> |16.0 hrs  <br/> |$272.00  <br/> |
|ProjectB  <br/> |T2  <br/> |24.0 hrs  <br/> |$428.00  <br/> |24.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectB  <br/> |T3  <br/> |40.0 hrs  <br/> |$740.00  <br/> |40.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectB  <br/> |T4  <br/> |8.0 hrs  <br/> |$168.00  <br/> |8.0 hrs  <br/> |-8.0 hrs  <br/> |-$168.00  <br/> |
   
## Definition

```XML
<EntityType Name="Task">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="TaskId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Assignments" Relationship="ReportingData.Assignment_Task_Task_Assignments" ToRole="Assignment_Task" FromRole="Task_Assignments" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a task and navigation properties of that task. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and assignments, that are associated with a task. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a task query. **ProjectId** is the project GUID and **TaskId** is the task GUID. 
  
### Property elements

The following table lists the **Property** elements for the **Task** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Task**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**FlagStatus** <br/> |**Edm.Boolean** <br/> |**true** <br/> ||
|**Health** <br/> |**Edm.String** <br/> |**true** <br/> |The Health assignment custom field.  <br/> |
|**ParentTaskId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a parent task.  <br/> |
|**ParentTaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a parent task.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**TaskActualCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost for work that has already been performed on a task, along with any other recorded costs.  <br/> |
|**TaskActualDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual working time for a task, based on the duration of the work that was performed on the task to completion.  <br/> |
|**TaskActualFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that a task was completed.  <br/> |
|**TaskActualFixedCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs for a task that remain constant regardless of the task duration, the amount of work performed by the resource, and the number of assignment units.  <br/> |
|**TaskActualOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost incurred for overtime work that has already been performed on a task.  <br/> |
|**TaskActualOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of overtime work that has already been performed on a task.  <br/> |
|**TaskActualRegularCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of regular, non-overtime work that has already been performed on a task.  <br/> |
|**TaskActualRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The regular, non-overtime work that has already been performed on a task.  <br/> |
|**TaskActualStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that a task actually began.  <br/> |
|**TaskActualWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual work that has already been performed on a task, usually expressed as the percent complete.  <br/> |
|**TaskACWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual cost of work that has already been performed on a task, up to the current date or status date.  <br/> |
|**TaskBCWP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work that has already been performed on a task, up to the current date or the status date.  <br/> |
|**TaskBCWS** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The budgeted cost of work scheduled, up to the current date or the status date.  <br/> |
|**TaskBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The scheduled costs.  <br/> |
|**TaskBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The scheduled work.  <br/> |
|**TaskClientUniqueId** <br/> |**Edm.Int32** <br/> |**false** <br/> |The GUID of a task client.  <br/> |
|**TaskCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total scheduled or projected cost for a task.  <br/> |
|**TaskCostVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between the baseline cost and total cost for a task.  <br/> |
|**TaskCPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The Cost Performance Index, calculated by dividing the budgeted cost of work performed by the actual cost of work scheduled.  <br/> |
|**TaskCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a task was added to the project.  <br/> |
|**TaskCreatedRevisionCounter** <br/> |**Edm.Int32** <br/> |**false** <br/> |Represents the number of times that a task has been modified.  <br/> |
|**TaskCV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The task earned value cost variance.  <br/> |
|**TaskCVP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The task **CVP**, calculated by dividing the task cost variance by the task budgeted cost of work performed.  <br/> |
|**TaskDeadline** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The target date and time for when a task should be completed.  <br/> |
|**TaskDeliverableFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The published deliverable finish date and time for a task.  <br/> |
|**TaskDeliverableStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The published deliverable start date and time for a task.  <br/> |
|**TaskDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total span of active working time for a task.  <br/> |
|**TaskDurationIsEstimated** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if task duration is estimated.  <br/> |
|**TaskDurationString** <br/> |**Edm.String** <br/> |**true** <br/> |The string value for the duration of a task.  <br/> |
|**TaskDurationVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between the baseline duration and the total duration (current estimate) of a task.  <br/> |
|**TaskEAC** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The task estimate at completion—the expected total cost of a task based on performance up to the status date.  <br/> |
|**TaskEarlyFinish** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The earliest date and time that a task can finish.  <br/> |
|**TaskEarlyStart** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The earliest date and time that a task can begin.  <br/> |
|**TaskFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that a task is scheduled to be completed.  <br/> |
|**TaskFinishDateString** <br/> |**Edm.String** <br/> |**true** <br/> |The string value of the task finish date and time.  <br/> |
|**TaskFinishVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Task variance at the finish date and time.  <br/> |
|**TaskFixedCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |A set cost for a task that remains constant regardless of the task duration or the work performed by a resource.  <br/> |
|**TaskFixedCostAssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the fixed cost assignment.  <br/> |
|**TaskFreeSlack** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of time a task can be delayed without delaying successor tasks.  <br/> |
|**TaskHyperLinkAddress** <br/> |**Edm.String** <br/> |**true** <br/> |A hyperlink that is associated with a task.  <br/> |
|**TaskHyperLinkFriendlyName** <br/> |**Edm.String** <br/> |**true** <br/> |The text to display for a task hyperlink.  <br/> |
|**TaskHyperLinkSubAddress** <br/> |**Edm.String** <br/> |**true** <br/> |The subaddress of a task hyperlink.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a task.  <br/> |
|**TaskIgnoresResourceCalendar** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task ignores resource calendars.  <br/> |
|**TaskIndex** <br/> |**Edm.Int32** <br/> |**true** <br/> |The number of a task in the local project.  <br/> |
|**TaskIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is active.  <br/> |
|**TaskIsCritical** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if a task is on a critical path.  <br/> |
|**TaskIsEffortDriven** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is effort-driven.  <br/> |
|**TaskIsExternal** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is linked from another project.  <br/> |
|**TaskIsManuallyScheduled** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is manually scheduled.  <br/> |
|**TaskIsMarked** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is marked.  <br/> |
|**TaskIsMilestone** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if a task is a milestone.  <br/> |
|**TaskIsOverallocated** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if a task is overallocated.  <br/> |
|**TaskIsProjectSummary** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if a task is a project summary task.  <br/> |
|**TaskIsRecurring** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a task is part of a series of recurring tasks.  <br/> |
|**TaskIsSummary** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if a task is a summary task.  <br/> |
|**TaskLateFinish** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The latest date and time that a task can finish without delaying the project finish.  <br/> |
|**TaskLateStart** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The latest date and time that a task can start without delaying the project finish date.  <br/> |
|**TaskLevelingDelay** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of time that a task is to be delayed from its early start date as a result of resource leveling.  <br/> |
|**TaskModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a task was modified.  <br/> |
|**TaskModifiedRevisionCounter** <br/> |**Edm.Int32** <br/> |**false** <br/> |The number of times that task data has been modified.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a task.  <br/> |
|**TaskOutlineLevel** <br/> |**Edm.Int16** <br/> |**true** <br/> |The position of a task in the project outline hierarchy, as indicated by a number.  <br/> |
|**TaskOutlineNumber** <br/> |**Edm.String** <br/> |**true** <br/> |The position of a task in the project outline hierarchy, as indicated by a text value.  <br/> |
|**TaskOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of overtime work on a task.  <br/> |
|**TaskOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of overtime work scheduled to be performed by all resources that are assigned to a task.  <br/> |
|**TaskPercentCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The current task status, expressed as the percent of the task duration that is completed.  <br/> |
|**TaskPercentWorkCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The current status of a task, expressed as the percentage of work completed.  <br/> |
|**TaskPhysicalPercentCompleted** <br/> |**Edm.Int16** <br/> |**true** <br/> |The percentage of a task that is completed. Used for calculating earned value ( **BCWP**.  <br/> |
|**TaskPriority** <br/> |**Edm.Int16** <br/> |**true** <br/> |The level of importance of a task, represented by a value from 0 to 1000.  <br/> |
|**TaskRegularCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of the regular, nonovertime work on a task.  <br/> |
|**TaskRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The regular, nonovertime work on a task.  <br/> |
|**TaskRemainingCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of the work that remains to be done on a task.  <br/> |
|**TaskRemainingDuration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The duration of the work that remains to be done on a task.  <br/> |
|**TaskRemainingOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of the overtime work that remains to be done on a task.  <br/> |
|**TaskRemainingOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The overtime work that remains to be done on a task.  <br/> |
|**TaskRemainingRegularCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost of the regular, nonovertime work that remains to be performed on a task.  <br/> |
|**TaskRemainingRegularWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The regular, nonovertime work that remains to be performed on a task.  <br/> |
|**TaskRemainingWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The work that remains to be done on a task.  <br/> |
|**TaskResourcePlanWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total work of all resources on tasks.  <br/> |
|**TaskSPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |A value that indicates whether the project is on schedule, calculated by dividing budgeted cost of work performed by the budgeted cost of work scheduled.  <br/> |
|**TaskStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that an assigned resource is scheduled to begin work on a task.  <br/> |
|**TaskStartDateString** <br/> |**Edm.String** <br/> |**true** <br/> |The string value for a task start date and time.  <br/> |
|**TaskStartVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Task start variance is the difference between a baseline start date and the currently scheduled start date.  <br/> |
|**TaskSV** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Task schedule variance is the cost difference between the current progress and the baseline plan of a task.  <br/> |
|**TaskSVP** <br/> |**Edm.Decimal** <br/> |**true** <br/> |Task schedule variance percentage (schedule variance divided by the TaskBCWS).  <br/> |
|**TaskTCPI** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The cost performance index (the ratio of the work that remains to be done, to funds remaining to be spent) as of the task status date.  <br/> |
|**TaskTotalSlack** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of time that a task finish date can be delayed without delaying the project finish date.  <br/> |
|**TaskVAC** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The task variance at completion of the task.  <br/> |
|**TaskWBS** <br/> |**Edm.String** <br/> |**true** <br/> |Work breakdown structure code that is used to represent the task position within the hierarchical structure of a project.  <br/> |
|**TaskWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total time scheduled on a task for all assigned resources.  <br/> |
|**TaskWorkVariance** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The difference between baseline work and currently scheduled work.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Prioritization** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Assignments** navigation property, the primary type is **Assignment**, and the secondary type is **Task**. For this type of navigation, the **FromRole** is **Assignment_Task**, and the **ToRole** is **Task_Assignments**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Assignments** <br/> |[Assignment_Task_Task_Assignments](association-assignment_task_task_assignments-projectdata-service.md) <br/> |Establishes navigation from a collection of assignments to a task and from a task to a collection of assignments.  <br/> |
|**AssignmentsBaselines** <br/> |[AssignmentBaseline_Task_Task_AssignmentsBaselines](association-element-assignmentbaseline_task-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignment baselines to a task and from a task to a collection of assignment baselines.  <br/> |
|**AssignmentsBaselineTimephasedData** <br/> |[AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData](association-assignmentbaselinetimephaseddata_tasks_task_assignmentsbaselinetimep.md) <br/> |Establishes navigation from a collection of assignment baseline timephased data to a task and from a task to a collection of assignment baseline timephased data.  <br/> |
|**Baselines** <br/> |[TaskBaseline_Task_Task_Baselines](association-element-taskbaseline_task-projectserverdata-service.md) <br/> |Establishes navigation from a collection of task baselines to a task and from a task to a collection of task baselines.  <br/> |
|**BaselinesTimephasedDataSet** <br/> |[TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet](association-taskbaselinetimephaseddata_task_task_baselinestimephaseddataset-proj.md) <br/> |Establishes navigation from a collection of task baseline timephased data to a task and from a task to a collection of task baseline timephased data.  <br/> |
|**Issues** <br/> |**Issue_Tasks_Task_Issues** <br/> ||
|**Project** <br/> |[Project_Tasks_Task_Project](association-project_tasks_task_project-projectdata-service.md) <br/> |Establishes navigation from a project to a collection of tasks and from a collection of tasks to a project.  <br/> |
|**Risks** <br/> |[Risk_Tasks_Task_Risks](association-element-risk_trigeringtasks-projectserverdata-service.md) <br/> ||
|**TimephasedInfo** <br/> |[TaskTimephasedData_Task_Task_TimephasedInfo](association-tasktimephaseddata_task_task_timephasedinfo-projectdata-service.md) <br/> |Establishes navigation from a collection of task timephased data to a task and from a task to a collection of task timephased data.  <br/> |
   
## See also

#### Reference

[Tasks](entityset-tasks-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

