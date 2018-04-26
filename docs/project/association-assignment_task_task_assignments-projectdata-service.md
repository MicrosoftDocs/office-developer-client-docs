---
title: "Association Assignment_Task_Task_Assignments (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f1f72c30-dc0e-4766-991a-eed774578467
description: "The Assignment_Task_Task_Assignment association relates assignments to the task that contains them and relates a task to its assignments."
---

# Association: Assignment_Task_Task_Assignments (ProjectData service)

The **Assignment_Task_Task_Assignment** association relates assignments to the task that contains them and relates a task to its assignments. 
  
## Definition

```XML
<Association Name="Assignment_Task_Task_Assignments">
  <End Type="ReportingData.Task" Role="Task_Assignments" Multiplicity="0..1" />
  <End Type="ReportingData.Assignment" Role="Assignment_Task" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Assignment_Task_Task_Assignments** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignments and tasks. In the first half of the name, **Assignment** is the entity type and **Task** is the navigation property. In the second half of the name, **Task** is the entity type and **Assignment** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Assignment_Task_Task_Assignment** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Assignment_Task_Task_Assignment association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Assignment_Task** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**\*** <br/> |There can be multiple assignment entities that correspond to a task.  <br/> |
|**Task_Assignment** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is one task that corresponds to a collection of assignments.  <br/> |
   
## Remarks

One end of the association is the **Assignment** entity, and the other end is the **Task** entity. The **Assignment** entity type contains the **Task** navigation property, where the **FromRole** defines **Assignment_Task** as the start of the association to get the collection of tasks that are associated with an assignment. Similarly, the **Task** entity type contains the **Assignment** navigation property, where the **FromRole** defines **Task_Assignment** as the start of the association to get the collection of assignments that is associated with a task. 
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

