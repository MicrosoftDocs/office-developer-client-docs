---
title: "Association element Risk_TrigeringTasks (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f82fe4ee-b0c5-49a0-bfeb-57c4dfbf59db
description: "The Risk_Tasks_Task_Risks association relates risks to tasks and relates tasks to risks."
---

# Association element: Risk_TrigeringTasks (ProjectServerData service)

The **Risk_Tasks_Task_Risks** association relates risks to tasks and relates tasks to risks. 
  
## Definition

```XML
<Association Name="Risk_Tasks_Task_Risks">
  <End Type="ReportingData.Task" Role="Task_Risks" Multiplicity="*" />
  <End Type="ReportingData.Risk" Role="Risk_Tasks" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Risk_Tasks_Task_Risks** <br/> |Identifies the entity types that form the **Risk_Tasks_Task_Risks** association for risks and tasks. In the first half of the name, Risk is the entity type and Tasks is the navigation property. In the second half of the name, Task is the entity type and Risks is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Risk_Tasks_Task_Risks** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Risk_Tasks_Task_Risks association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Risk_Tasks** <br/> |[EntityType: Risk](entitytype-risk-projectdata-service.md) <br/> |**\*** <br/> |The collection of risks in the reporting tables.  <br/> |
|**Task_Risks** <br/> |[EntityType: Task](entitytype-task-projectdata-service.md) <br/> |**\*** <br/> |The collection of tasks in the reporting tables.  <br/> |
   
## Remarks

The **Risk_Tasks_Task_Risks** association is used by the **Risk_Tasks** navigation property to query tasks that are associated with a risk, and the **Task_Risks** navigation property to query risks that are associated with a task. 
  
## See also

#### Reference

[EntityType: Risk](entitytype-risk-projectdata-service.md)
  
[EntityType: Task](entitytype-task-projectdata-service.md)

