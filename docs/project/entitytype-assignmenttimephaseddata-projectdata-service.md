---
title: "EntityType AssignmentTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 70226cb1-11ee-4ab7-948b-03c7ab7225c1
description: "Contains the properties that define the reporting data for assignment timephased data in the ProjectData service."
---

# EntityType: AssignmentTimephasedData (ProjectData service)

Contains the properties that define the reporting data for assignment timephased data in the **ProjectData** service. 
  
## Example

The following REST query uses the [AssignmentTimephasedDataSet](entityset-assignmenttimephaseddataset-projectdata-service.md) entity set and the **ProjectId** and **TimeByDay** keys to get the specified collection of assignment timephased data in **ProjectData**. The query is all on one line.
  
```
http://<pwa_url>/_api/ProjectData/AssignmentTimephasedDataSet
    ?$filter=ProjectId eq guid'3a9acc04-3ce6-e111-9724-00155d344f1a'
    and TimeByDay gt datetime'2012-01-01'
```

## Definition

```XML
<EntityType Name="AssignmentTimephasedData">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="AssignmentId" />
    <PropertyRef Name="TimeByDay" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Assignment" Relationship="ReportingData.AssignmentTimephasedData_Assignment_Assignment_TimephasedData" ToRole="Assignment_TimephasedData" FromRole="AssignmentTimephasedData_Assignment" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of assignment timephased data and navigation properties of that assignment timephased data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and assignments, that are associated with assignment timephased data. A navigation property uses an **Association** element in a query for a related entity or collection. 
  
The **Key** elements specify the properties that are the primary keys for a query for assignment timephased data. **ProjectId** is the project GUID, **AssignmentId** is the GUID for the assignment, and **TimeByDay** is a day in the timeline. 
  
### Property elements

The following table lists the values of the **Property** elements for the **AssignmentTimephasedData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of AssignmentTimephasedData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentActualCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for work that has already been performed on an assignment, along with any other associated costs.  <br/> |
|**AssignmentActualOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The costs incurred for overtime work that has already been performed on an assignment.  <br/> |
|**AssignmentActualOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The actual amount of overtime work that has already been performed on an assignment.  <br/> |
|**AssignmentActualRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of the nonovertime work that has already been performed on an assignment.  <br/> |
|**AssignmentActualRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual amount of regular, nonovertime work that has already been performed on an assignment.  <br/> |
|**AssignmentActualWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The amount of work that has already been performed on an assignment.  <br/> |
|**AssignmentBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total projected cost of an assignment.  <br/> |
|**AssignmentBudgetMaterialWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total projected amount of use on the assignment of material resources.  <br/> |
|**AssignmentBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total projected amount of work that is planned for an assignment.  <br/> |
|**AssignmentCombinedWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The work for the assignment, from both the project plan and the resource plan.  <br/> |
|**AssignmentCost** <br/> |**Edm.Int32** <br/> |**true** <br/> |The total cost for an assignment, based on costs already incurred, in addition to costs that are planned for the remaining work.  <br/> |
|**AssignmentCumulativeActualWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The summation of the work that has already been performed on an assignment.  <br/> |
|**AssignmentCumulativeCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The summation of the cost of an assignment.  <br/> |
|**AssignmentCumulativeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The summation of the amount of time, such as person-hours or days, that has accumulated on an assignment.  <br/> |
|**AssignmentId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the assignment.  <br/> |
|**AssignmentMaterialActualWork** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The actual amount of work that has already been performed with the use of a material resource, usually expressed as a percentage of the scheduled amount of material resource work.  <br/> |
|**AssignmentMaterialWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total work time scheduled for a material resource.  <br/> |
|**AssignmentOvertimeCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total overtime cost for an assignment, including costs for overtime work that has already been performed, in addition to remaining overtime costs.  <br/> |
|**AssignmentOvertimeWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total overtime work for an assignment, including overtime work that has already been performed, in addition to remaining overtime work.  <br/> |
|**AssignmentRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total cost for regular, nonovertime assignment work that has already been performed, in addition to remaining nonovertime work.  <br/> |
|**AssignmentRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total nonovertime work for an assignment (including regular, nonovertime work that has already been performed), in addition to remaining regular, nonovertime work.  <br/> |
|**AssignmentRemainingCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The scheduled expense that will be incurred in completing the remaining work on the assignment.  <br/> |
|**AssignmentRemainingCumulativeActualWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cumulative total amount of remaining scheduled work.  <br/> |
|**AssignmentRemainingCumulativeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cumulative total amount of remaining work.  <br/> |
|**AssignmentRemainingOvertimeCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining overtime expense for an assignment.  <br/> |
|**AssignmentRemainingOvertimeWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The remaining overtime work for an assignment.  <br/> |
|**AssignmentRemainingRegularCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The expense that will be incurred by completing the remaining regular, nonovertime work for an assignment.  <br/> |
|**AssignmentRemainingRegularWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of time, such as person-hours or days, that is still required to complete the regular, nonovertime work for an assignment.  <br/> |
|**AssignmentRemainingWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of time, such as person-hours or days, that is still required to complete both regular and overtime work for an assignment.  <br/> |
|**AssignmentResourcePlanWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The total time that is scheduled for an assignment in the resource plan.  <br/> |
|**AssignmentWork** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total amount of time, such as person-hours or days, that is scheduled for an assignment.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the project for the assignment timephased data.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**ResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the resource for the assignment timephased data.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies the task for the assignment timephased data.  <br/> |
|**TaskIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the task for the assignment timephased data is active.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a task.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies a day along a timeline. The granularity is in days only.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **AssignmentTimephasedData** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Assignment** navigation property, the primary type is **AssignmentTimephasedData**, and the secondary type is **Assignment**. For this type of navigation, the **FromRole** is **AssignmentTimephasedData_Assignment**, and the **ToRole** is **Assignment_TimephasedData**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **AssignmentBaselineTimephasedData** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Assignment** <br/> |[AssignmentTimephasedData_Assignment_Assignment_TimephasedData](association-element-assignment_timephaseddata-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignment timephased data to an assignment and from an assignment to a timephased data entity.  <br/> |
|**Project** <br/> |[AssignmentTimephasedData_Project](association-assignmenttimephaseddata_project-projectdata-service.md) <br/> |Establishes navigation from a collection of assignment timephased data to a project.  <br/> |
|**Task** <br/> |[AssignmentTimephasedData_Task](association-element-assignmenttimephaseddata_task-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignment timephased data to a task.  <br/> |
   
## See also

#### Reference

[AssignmentTimephasedDataSet](entityset-assignmenttimephaseddataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

