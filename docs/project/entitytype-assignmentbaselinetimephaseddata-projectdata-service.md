---
title: "EntityType AssignmentBaselineTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: cf0514e5-0e33-43e9-8f2e-9a8d06ff7673
description: "Contains the properties that define the reporting data for assignment baseline timephased data in the ProjectData service."
---

# EntityType: AssignmentBaselineTimephasedData (ProjectData service)

Contains the properties that define the reporting data for assignment baseline timephased data in the **ProjectData** service. 
  
## Example

The following REST query uses the [AssignmentBaselineTimephasedDataSet](entityset-assignmentbaselinetimephaseddataset-projectdata-service.md) entity set with the **AssignmentId** and **ProjectId** keys to get the specified assignment baseline timephased dataset. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/AssignmentBaselineTimephasedDataSet
    ?$filter=AssignmentId eq guid'7ffecbe8-ada6-e111-9f30-78e7d101788a'
    and ProjectId eq guid'76fecbe8-ada6-e111-9f30-78e7d101788a'
```

## Definition

```XML
<EntityType Name="AssignmentBaselineTimephasedData">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="AssignmentId" />
    <PropertyRef Name="TimeByDay" />
    <PropertyRef Name="BaselineNumber" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Assignment" Relationship="ReportingData.AssignmentBaselineTimephasedData_Assignment" ToRole="Assignment" FromRole="AssignmentBaselineTimephasedData" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of assignment baseline timephased data and navigation properties of that assignment baseline timephased data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as baselines and projects, that are associated with timephased data for an assignment. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a query for assignment baseline timephased data. **ProjectId** is the project GUID, **AssignmentId** is the GUID of the assignment, **TimeByDay** is a day in the timeline, and **BaselineNumber** is the number of the assignment baseline. 
  
### Property elements

The following table lists the values of the **Property** elements for the **AssignmentBaselineTimephasedData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute Values for the Property elements of AssignmentBaselineTimephasedData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaselineBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned cost of an assignment.  <br/> |
|**AssignmentBaselineBudgetMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned number of units of the supplies or other consumable items that are to be used to complete an assignment.  <br/> |
|**AssignmentBaselineBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned total amount of time that is needed to complete an assignment.  <br/> |
|**AssignmentBaselineCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned cost of the assignment.  <br/> |
|**AssignmentBaselineCumulativeCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The original estimated cumulative timephased baseline costs of an assignment up to the status date or today's date.  <br/> |
|**AssignmentBaselineCumulativeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The original estimated cumulative timephased baseline work on an assignment up to the status date or today's date.  <br/> |
|**AssignmentBaselineMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned number of units of supplies or other consumable items that are to be used to complete an assignment.  <br/> |
|**AssignmentBaselineRemainingCumulativeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The current remaining amount of timephased baseline work on an assignment up to the status date or today's date.  <br/> |
|**AssignmentBaselineWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total planned person-hours scheduled for an assignment.  <br/> |
|**AssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the assignment.  <br/> |
|**BaselineNumber** <br/> |**Edm.Int32** <br/> |**False** <br/> |**Key**         An integer number that identifies a baseline in a project.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the project that is associated with the assignment baseline timephased data.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project that is associated with the assignment baseline timephased data.  <br/> |
|**ResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the resource.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the task that is associated with the assignment baseline timephased data.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies a day along a timeline. The granularity is in days only.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **AssignmentBaselineTimephasedData** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Tasks** navigation property, the primary type is **AssignmentBaselineTimephasedData**, and the secondary type is **Task**. For this type of navigation, the **FromRole** is **AssignmentBaselineTimephasedData_Tasks**, and the **ToRole** is **Task_AssignmentsBaselineTimephasedData**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Assignment** navigation property relationship, **AssignmentBaselineTimephasedData** is the primary entity type and **Assignment** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Assignment** <br/> |[AssignmentBaselineTimephasedData_Assignment](association-assignmentbaselinetimephaseddata_assignment-projectdata-service.md) <br/> |Establishes navigation from a collection of assignment baselines to an assignment.  <br/> |
|**Baseline** <br/> |[AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline](association-assignmentbaseline_assignmentbaselinetimephaseddataset_assignmentbas.md) <br/> |Establishes navigation from an assignment baseline to an assignment baseline timephased dataset and from a collection of assignment baseline timephased data to a baseline.  <br/> |
|**Project** <br/> |[AssignmentBaselineTimephasedData_Project](association-element-assignmentbaselinetimephaseddata_project-projectserverdata-s.md) <br/> |Establishes navigation from a collection of assignment baseline timephased data to a project.  <br/> |
|**Tasks** <br/> |[AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData](association-assignmentbaselinetimephaseddata_tasks_task_assignmentsbaselinetimep.md) <br/> |Establishes navigation from a collection of assignment baseline timephased data to a task and from a task to a collection of assignment baseline timephased data.  <br/> |
   
## See also

#### Reference

[AssignmentBaselineTimephasedDataSet](entityset-assignmentbaselinetimephaseddataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

