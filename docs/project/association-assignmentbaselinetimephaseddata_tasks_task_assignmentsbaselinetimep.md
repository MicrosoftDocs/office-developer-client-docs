---
title: "Association AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 2596b256-bb09-4295-9a62-cefc9a96b557
description: "The AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData association relates timephased data for assignment baselines to a task and relates a task to timephased data for assignment baselines."
---

# Association: AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData (ProjectData service)

The **AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData** association relates timephased data for assignment baselines to a task and relates a task to timephased data for assignment baselines. 
  
## Definition

```XML
<Association Name="AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData">
  <End Type="ReportingData.Task" Role="Task_AssignmentsBaselineTimephasedData" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentBaselineTimephasedData" Role="AssignmentBaselineTimephasedData_Tasks" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignment baseline timephased data and tasks. In the first half of the name, **AssignmentBaselineTimephasedData** is the entity type and **Tasks** is the navigation property. In the second half of the name, **Task** is the entity type and **AssignmentsBaselineTimephasedData** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaselineTimephasedData_Tasks_Task_AssignmentsBaselineTimephasedData association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaselineTimephasedData_Tasks** <br/> |[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be multiple collections of assignment baseline timephased data that correspond to a task.  <br/> |
|**Task_AssignmentsBaselineTimephasedData** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There can one task that corresponds to a collection of assignment baseline timephased data.  <br/> |
   
## Remarks

One end of the association is the **AssignmentBaselineTimephasedData** entity, and the other end is the **Task** entity. The **AssignmentBaselineTimephasedData** entity type contains the **Tasks** navigation property, where the **FromRole** defines **AssignmentBaselineTimephasedData_Tasks** as the start of the association to get a task that is associated with collections of assignment baseline timephased data. Similarly, the **Task** entity type contains the **AssignmentsBaselineTimephasedData** navigation property, where the **FromRole** defines **Task_AssignmentsBaselineTimephasedData** as the start of the association to get assignment baseline timephased data that is associated with a task. 
  
## See also

#### Reference

[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

