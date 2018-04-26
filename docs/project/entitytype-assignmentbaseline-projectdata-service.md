---
title: "EntityType AssignmentBaseline (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b589eda2-804b-46d1-afab-6216f46455ba
description: "Contains the properties that define the reporting data for an assignment baseline in the ProjectData service."
---

# EntityType: AssignmentBaseline (ProjectData service)

Contains the properties that define the reporting data for an assignment baseline in the **ProjectData** service. 
  
## Example

The following REST query uses the [AssignmentBaselines](entityset-assignmentbaselines-projectdata-service.md) entity set with the **AssignmentId**, **BaselineNumber**, and **ProjectId** keys to get the specified baseline. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/AssignmentBaselines
    ?$filter=AssignmentId eq guid'a85aaf31-c2f2-e111-9b73-001aa0d20198'
    and BaselineNumber eq 2
    and ProjectId eq guid'd8ef483f-c2f2-e111-9b73-001aa0d20198'
```

## Definition

```XML
<EntityType Name="AssignmentBaseline">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="AssignmentId" />
    <PropertyRef Name="BaselineNumber" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Assignment" Relationship="ReportingData.AssignmentBaseline_Assignment_Assignment_Baseline" ToRole="Assignment_Baseline" FromRole="AssignmentBaseline_Assignment" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of an assignment baseline and navigation properties of that assignment baseline. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and projects, that are associated with an assignment baseline. A navigation property uses an **Association** element in a query for a related entity or collection. 
  
The **Key** elements specify the properties that are the primary key for an assignment baseline query. **ProjectId** is the project GUID, **AssignmentId** is the GUID of the assignment, and **BaselineNumber** is the identifying number of the assignment baseline. 
  
### Property elements

The following table lists the values of the **Property** elements for the **AssignmentBaseline** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of AssignmentBaseline**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaselineBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of the originally planned budget for the assignment.  <br/> |
|**AssignmentBaselineBudgetMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The original, estimated, and budgeted number of units of the supplies or other consumable items that are used to complete an assignment.  <br/> |
|**AssignmentBaselineBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of work scheduled in the planned budget for the assignment.  <br/> |
|**AssignmentBaselineCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned total cost for an assignment.  <br/> |
|**AssignmentBaselineFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The planned finish date of the assignment.  <br/> |
|**AssignmentBaselineMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The number of units of supplies or other consumable items that are planned to be used to complete an assignment.  <br/> |
|**AssignmentBaselineStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The planned start date of the assignment.  <br/> |
|**AssignmentBaselineWork** <br/> |**Edm. Decimal** <br/> |**false** <br/> |The planned amount of work for the assignment.  <br/> |
|**AssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the assignment.  <br/> |
|**AssignmentType** <br/> |**Edm.Int32** <br/> |**false** <br/> |An enumerated value that represents the type of assignment.  <br/> |
|**BaselineNumber** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         A number that identifies an assignment baseline.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the task.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **AssignmentBaseline** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Assignment** navigation property, the primary type is **AssignmentBaseline**, and the secondary type is **Assignment**. For this type of navigation, the **FromRole** is **AssignmentBaseline_Assignment**, and the **ToRole** is **Assignment_Baseline**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Assignment** <br/> |[AssignmentBaseline_Assignment_Assignment_Baseline](association-assignmentbaseline_assignment_assignment_baseline-projectdata-servic.md) <br/> |Establishes navigation from a collection of assignment baselines to an assignment and from an assignment to a collection of baselines.  <br/> |
|**AssignmentBaselineTimephasedDataSet** <br/> |[AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline](association-assignmentbaseline_assignmentbaselinetimephaseddataset_assignmentbas.md) <br/> |Establishes navigation from an assignment baseline to a collection of assignment baseline timephased data and from an assignment baseline timephased data entity to a baseline.  <br/> |
|**Project** <br/> |[Project_AssignmentBaselines_AssignmentBaseline_Project](association-element-project_assignmentbaselines-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of assignment baselines and from an assignment baseline to a project.  <br/> |
|**Task** <br/> |[AssignmentBaseline_Task_Task_AssignmentsBaselines](association-element-assignmentbaseline_task-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignment baselines to a task and from a task to a collection of assignment baselines.  <br/> |
   
## See also

#### Reference

[AssignmentBaselines](entityset-assignmentbaselines-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

