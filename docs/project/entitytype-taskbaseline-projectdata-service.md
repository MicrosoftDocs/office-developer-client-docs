---
title: "EntityType TaskBaseline (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: b8199dc1-d8e6-4fb1-b3f1-dd88b7d2a230
description: "Contains the properties that define the reporting data for a project in the ProjectData service."
---

# EntityType: TaskBaseline (ProjectData service)

Contains the properties that define the reporting data for a project in the **ProjectData** service. 
  
## Example

The following REST query uses the [TaskBaselines](entityset-taskbaselines-projectdata-service.md) entity set and the **BaselineNumber**, **ProjectId**, and **TaskId** keys to get the specified task baseline. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/TaskBaselines
    ?$filter=BaselineNumber eq 1
    and ProjectId eq guid'76fecbe8-ada6-e111-9f30-78e7d101788a'
    and TaskId eq guid'79fecbe8-ada6-e111-9f30-78e7d101788a'
```

## Definition

```XML
<EntityType Name="TaskBaseline">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="TaskId" />
    <PropertyRef Name="BaselineNumber" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.TaskBaseline_Project" ToRole="Project" FromRole="TaskBaseline" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a task baseline and navigation properties of that task baseline. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and projects, that are associated with a project. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a task baseline query. **ProjectId** is the project GUID, **TaskId** is the task GUID, and **BaselineNumber** is the number of the task baseline. 
  
### Property elements

The following table lists the **Property** elements for the **TaskBaseline** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of TaskBaseline**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BaselineNumber** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         A number that identifies a project baseline.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**TaskBaselineBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of the budgeted amount of work as projected in the baseline.  <br/> |
|**TaskBaselineBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The budgeted amount of work as projected in the baseline.  <br/> |
|**TaskBaselineCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total planned cost for a task. The baseline cost is known as budget at completion ( **BAC**) for earned value.  <br/> |
|**TaskBaselineDeliverableFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The published deliverable finish date and time for a task as projected in the baseline.  <br/> |
|**TaskBaselineDeliverableStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The published deliverable start date and time for a task.  <br/> |
|**Task BaselineDuration** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of time estimated to complete a task.  <br/> |
|**TaskBaselineDurationString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains the projected task duration.  <br/> |
|**TaskBaselineFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The projected completion date of a task.  <br/> |
|**TaskBaselineFinishDateString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains the projected task finish date and time.  <br/> |
|**TaskBaselineFixedCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |A set task cost that is projected in the baseline and that remains constant regardless of the task duration or the work performed by a resource.  <br/> |
|**TaskBaselineStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The projected task start date and time.  <br/> |
|**TaskBaselineStartDateString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains the projected task start date and time.  <br/> |
|**TaskBaselineWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total hours that are scheduled in the baseline projection for a task.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **TaskBaseline** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Task** navigation property, the primary type is **TaskBaseline**, and the secondary type is **Task**. For this type of navigation, the **FromRole** is **TaskBaseline_Task**, and the **ToRole** is **Task_Baselines**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **TaskBaseline** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[TaskBaseline_Project](association-element-taskbaseline_project-projectserverdata-service.md) <br/> |Establishes navigation from a collection of task baselines to a project.  <br/> |
|**Task** <br/> |[TaskBaseline_Task_Task_Baselines](association-element-taskbaseline_task-projectserverdata-service.md) <br/> |Establishes navigation from a collection of task baselines to a task and from a task to a baseline.  <br/> |
|**TaskBaselineTimephasedDataSet** <br/> |[TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines](association-taskbaseline_taskbaselinetimephaseddataset_taskbaselinetimephaseddat.md) <br/> |Establishes navigation from a collection of task baselines to a collection of task baseline timephased data and from a collection of task baseline timephased data to a collection of task baselines.  <br/> |
   
## See also

#### Reference

[TaskBaselines](entityset-taskbaselines-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

