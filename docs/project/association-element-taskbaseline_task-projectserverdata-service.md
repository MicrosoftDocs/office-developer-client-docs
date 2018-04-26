---
title: "Association element TaskBaseline_Task (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 626d9f90-49b3-44f1-89e6-54d9fc0d313f
description: "The TaskBaseline_Task_Task_Baselines association relates a task to task baselines and relates task baselines to a task."
---

# Association element: TaskBaseline_Task (ProjectServerData service)

The **TaskBaseline_Task_Task_Baselines** association relates a task to task baselines and relates task baselines to a task. 
  
## Definition

```XML
<Association Name="TaskBaseline_Task_Task_Baselines">
  <End Type="ReportingData.Task" Role="Task_Baselines" Multiplicity="0..1" />
  <End Type="ReportingData.TaskBaseline" Role="TaskBaseline_Task" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaseline_Task_Task_Baselines** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and tasks. In the first half of the name, **TaskBaseline** is the entity type and **Task** is the navigation property. In the second half of the name, **Task** is the entity type and **Baselines** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskBaseline_Task_Task_Baselines** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskBaseline_Task_Task_Baselines association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskBaseline_Task** <br/> |[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md) <br/> |**\*** <br/> |There can be many task baseline entities that correspond with a task.  <br/> |
|**Task_Baselines** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is one task entity that corresponds to a collection of baselines.  <br/> |
   
## Remarks

One end of the association is the **TaskBaseline** entity, and the other end is the **Task** entity. The **TaskBaseline** entity type contains the **Task** navigation property, where the **FromRole** defines **TaskBaseline_Task** as the start of the association to get the task that is associated with a collection of task baselines. Similarly, the **Task** entity type contains the **Baselines** navigation property, where the **FromRole** defines **Task_Baselines** as the start of the association to get the collection of baselines that are associated with a task. 
  
## See also

#### Reference

[EntityType element: Task](entitytype-task-projectdata-service.md)
  
[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md)

