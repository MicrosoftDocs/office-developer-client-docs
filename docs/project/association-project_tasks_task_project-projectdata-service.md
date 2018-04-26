---
title: "Association Project_Tasks_Task_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 9b72a411-b62e-4050-a406-a7d6107e46d1
description: "The Project_Tasks_Task_Project association relates a project to the tasks that it contains and relates a task to its project."
---

# Association: Project_Tasks_Task_Project (ProjectData service)

The **Project_Tasks_Task_Project** association relates a project to the tasks that it contains and relates a task to its project. 
  
## Definition

```XML
<Association Name="Project_Tasks_Task_Project">
  <End Type="ReportingData.Task" Role="Task_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Tasks" Multiplicity="0..1" />
</Association>

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Tasks_Task_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and tasks. In the first half of the name, **Project** is the entity type and **Tasks** is the navigation property. In the second half of the name, **Task** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Tasks_Task_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Tasks_Task_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Tasks** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of tasks. Those tasks belong to the project.  <br/> |
|**Task_Project** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**\*** <br/> |There can be many task entities in a project (a project has at least one task, if you count the project summary task).  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Task** entity. The **Project** entity type contains the **Tasks** navigation property, where the **FromRole** defines **Project_Tasks** as the start of the association to get the collection of tasks in a project. Similarly, the **Task** entity type contains the **Project** navigation property, where the **FromRole** defines **Task_Project** as the start of the association to get the project that a task belongs to. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

