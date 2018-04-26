---
title: "Association TaskTimephasedData_Task_Task_TimephasedInfo (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: df6ed347-cf9b-4339-9657-f59615b2aaa3
description: "TaskTimephasedData_Task_Task_TimephasedInfo association relates a task timephased data to a task and relates a task to timephased information."
---

# Association: TaskTimephasedData_Task_Task_TimephasedInfo (ProjectData service)

 **TaskTimephasedData_Task_Task_TimephasedInfo** association relates a task timephased data to a task and relates a task to timephased information. 
  
## Definition

```XML
<Association Name="TaskTimephasedData_Task_Task_TimephasedInfo">
  <End Type="ReportingData.Task" Role="Task_TimephasedInfo" Multiplicity="0..1" />
  <End Type="ReportingData.TaskTimephasedData" Role="TaskTimephasedData_Task" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskTimephasedData_Task_Task_TimephasedInfo** <br/> |Identifies the entity types and the navigation properties that form the two-way association for task timephased data and tasks. In the first half of the name, **TaskTimephasedData** is the entity type and **Task** is the navigation property. In the second half of the name, **Task** is the entity type and **TimephasedInfo** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskTimephasedData_Task_Task_TimephasedInfo** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskTimephasedData_Task_Task_TimephasedInfo association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskTimephasedData_Task** <br/> |[EntityType element: TaskTimephasedData](entitytype-tasktimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be many task timephased data entities that correspond with a task.  <br/> |
|**Task_TimephasedInfo** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is one task entity that corresponds to a collection of task timephased data.  <br/> |
   
## Remarks

One end of the association is the **TaskTimephasedData** entity, and the other end is the **Task** entity. The **TaskTimephasedData** entity type contains the **Task** navigation property, where the **FromRole** defines **TaskTimephasedData_Task** as the start of the association to get the task that is associated with a collection of task timephased data. Similarly, the **Task** entity type contains the **TimephasedInfo** navigation property, where the **FromRole** defines **Task_TimephasedInfo** as the start of the association to get the collection of task timephased information that is associated with a task. 
  
## See also

#### Reference

[EntityType element: Task](entitytype-task-projectdata-service.md)
  
[EntityType element: TaskTimephasedData](entitytype-tasktimephaseddata-projectdata-service.md)

