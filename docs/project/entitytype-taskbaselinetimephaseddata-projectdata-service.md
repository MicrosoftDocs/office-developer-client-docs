---
title: "EntityType TaskBaselineTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 8f7ce023-0ce0-4ac2-8660-cc3f238c9d8c
description: "Contains the properties that define the reporting data for task baseline timephased data in the ProjectData service."
---

# EntityType: TaskBaselineTimephasedData (ProjectData service)

Contains the properties that define the reporting data for task baseline timephased data in the **ProjectData** service. 
  
## Example

The following REST query uses the [TaskBaselineTimephasedDataSet](entityset-taskbaselinetimephaseddataset-projectdata-service.md) entity set and the **ProjectId** and **TaskId** keys to get the task baseline timephased data for the specified project, task, and time range in **ProjectData**. The query is all on one line.
  
```
https://<pwa_url>/_api/ProjectData/TaskBaselineTimephasedDataSet
    ?$filter=ProjectId eq guid'adfb14b1-16ea-e211-9405-180373341b25'
    and TaskId eq guid'845683f0-c0ef-e211-be7c-0014225df633'
    and TimeByDay gt datetime'2014-06-30'
```

## Definition

```XML
<EntityType Name="TaskBaselineTimephasedData">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="TaskId" />
    <PropertyRef Name="TimeByDay" />
    <PropertyRef Name="BaselineNumber" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.TaskBaselineTimephasedData_Project" ToRole="Project" FromRole="TaskBaselineTimephasedData" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of task baseline timephased data and navigation properties of that timephased data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and task baselines, that are associated with a project. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a task baseline timephased data query. **ProjectId** is the project GUID, **TaskId** is the task GUID, **TimeByDay** is a day in the timeline, and **BaselineNumber** is the number of the task baseline. 
  
### Property elements

The following table lists the **Property** elements for the **TaskBaselineTimephasedData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of TaskBaselineTimephasedData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BaselineNumber** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         A number that identifies a project baseline.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**TaskBaselineBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of the planned, budgeted amount of work on a task.  <br/> |
|**TaskBaselineBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned, budgeted amount of work on a task.  <br/> |
|**TaskBaselineCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total planned cost for a task. The baseline cost is also known as budget at completion ( **BAC**) for earned value.  <br/> |
|**TaskBaselineFixedCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |A set task cost that is projected in the baseline and that remains constant regardless of the task duration or the work performed by a resource.  <br/> |
|**TaskBaselineWork** <br/> |**Edm.Decimal** **** <br/> |**false** <br/> |The total planned hours that are scheduled for a task in the baseline projection.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **TaskBaselineTimephasedData** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Task** navigation property, the primary type is **TaskBaselineTimephasedData**, and the secondary type is **Task**. For this type of navigation, the **FromRole** is **TaskBaselineTimephasedData_Task**, and the **ToRole** is **Task_BaselinesTimephasedDataSet**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **TaskBaselineTimephasedData** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[TaskBaselineTimephasedData_Project](association-element-taskbaselinetimephaseddata_project-projectserverdata-service.md) <br/> |Establishes navigation from a collection of task baseline timephased data to a project.  <br/> |
|**Task** <br/> |[TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet](association-taskbaselinetimephaseddata_task_task_baselinestimephaseddataset-proj.md) <br/> |Establishes navigation from a collection of task baseline timephased data to a task and from a task to a baseline timephased dataset.  <br/> |
|**TaskBaselines** <br/> |[TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines](http://msdn.microsoft.com/library/f5e226b2-6fce-4263-950d-234d5e308294%28Office.15%29.aspx) <br/> |Establishes navigation from a collection of task baselines to collection of task baseline timephased data and from a collection of task baseline timephased data to a task baseline.  <br/> |
   
## See also

#### Reference

[TaskBaselineTimephasedDataSet](entityset-taskbaselinetimephaseddataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

