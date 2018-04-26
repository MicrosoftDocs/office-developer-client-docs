---
title: "EntityType TaskTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 2a96747d-1ccf-42db-9a81-52c26defb565
description: "Contains the properties that define the reporting data for task timephased data in the ProjectData service."
---

# EntityType: TaskTimephasedData (ProjectData service)

Contains the properties that define the reporting data for task timephased data in the **ProjectData** service. 
  
## Example

The following REST query uses the [TaskTimephasedDataSet](entityset-tasktimephaseddataset-projectdata-service.md) and the **TaskId** key to get the timephased data set for the specified task and time range in the **ProjectData** service. The query is all on one line. 
  
```
 
https://<pwa_url>/_api/ProjectData/TaskTimephasedDataSet
    ?$filter=TaskId eq guid'845683f0-c0ef-e211-be7c-0014225df633'
    and TimeByDay gt datetime'2013-06-30'
```

## Definition

```XML
<EntityType Name="TaskTimephasedData">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="TaskId" />
    <PropertyRef Name="TimeByDay" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.TaskTimephasedData_Project" ToRole="Project" FromRole="TaskTimephasedData" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of task timephased data and navigation properties of that data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and projects, that are associated with task timephased data. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a task timephased data query. **ProjectId** is the project GUID, **TaskId** is the task GUID, **TimeByDay** is a day along the timeline. 
  
### Property elements

The following table lists the **Property** elements for the **TaskTimephasedData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of TaskTimephasedData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**TaskActualCost** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The costs incurred for work that is already performed by all resources on a task, along with any other recorded costs.  <br/> |
|**TaskActualWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual work that is already performed by resources on a task, usually expressed as percent complete.  <br/> |
|**TaskBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The scheduled costs for a task.  <br/> |
|**TaskBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The scheduled work for a task.  <br/> |
|**TaskCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total scheduled or projected cost for a task.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the task.  <br/> |
|**TaskIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the task is active.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
|**TaskOvertimeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of overtime work that is scheduled to be performed by all resources that are assigned to a task.  <br/> |
|**TaskResourcePlanWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total time that is scheduled for the task in the resource plan.  <br/> |
|**TaskWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total time that is scheduled for a task for all assigned resources.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **TaskTimephasedData** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Task** navigation property, the primary type is **TaskTimephasedData**, and the secondary type is **Task**. For this type of navigation, the **FromRole** is **TaskTimephasedData_Task**, and the **ToRole** is **Task_TimephasedInfo**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **TaskTimephasedData** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[TaskTimephasedData_Project](association-tasktimephaseddata_project-projectdata-service.md) <br/> |Establishes navigation from a collection of task timephased data to a project.  <br/> |
|**Task** <br/> |[TaskTimephasedData_Task_Task_TimephasedInfo](association-tasktimephaseddata_task_task_timephasedinfo-projectdata-service.md) <br/> |Establishes navigation from a collection of task timephased data to a task and from a task to a collection of task timephased data.  <br/> |
   
## See also

#### Reference

[TaskTimephasedDataSet](entityset-tasktimephaseddataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

