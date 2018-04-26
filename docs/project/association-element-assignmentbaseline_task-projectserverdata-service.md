---
title: "Association element AssignmentBaseline_Task (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 5c315c24-ca47-4f04-a651-1f486054d7a5
description: "The AssignmentBaseline_Task_Task_AssignmentsBaselines association relates assignment baselines to a task and relates a task to its assignment baselines."
---

# Association element: AssignmentBaseline_Task (ProjectServerData service)

The **AssignmentBaseline_Task_Task_AssignmentsBaselines** association relates assignment baselines to a task and relates a task to its assignment baselines. 
  
## Definition

```XML
<Association Name="AssignmentBaseline_Task_Task_AssignmentsBaselines">
  <End Type="ReportingData.Task" Role="Task_AssignmentsBaselines" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentBaseline" Role="AssignmentBaseline_Task" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaseline_Task_Task_AssignmentsBaselines** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignment baselines and tasks. In the first half of the name, **AssignmentBaseline** is the entity type and **Task** is the navigation property. In the second half of the name, **Task** is the entity type and **AssignmentsBaselines** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaseline_Task_Task_AssignmentsBaselines** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaseline_Task_Task_AssignmentsBaselines association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaseline_Task** <br/> |[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md) <br/> |**\*** <br/> |There can be multiple assignment baseline entities that correspond to a task.  <br/> |
|**Task_AssignmentsBaselines** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is be one task entity that can be associated with multiple assignment baselines.  <br/> |
   
## Remarks

One end of the association is the **AssignmentBaseline** entity, and the other end is the **Task** entity. The **AssignmentBaseline** entity type contains the **Task** navigation property, where the **FromRole** defines **AssignmentBaseline_Task** as the start of the association to get the collection of assignment baselines that are associated with a task. Similarly, the **Task** entity type contains the **AssignmentsBaselines** navigation property, where the **FromRole** defines **Task_AssignmentsBaselines** as the start of the association to get the task that is associated with a collection of assignment baseline. 
  
## See also

#### Reference

[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

