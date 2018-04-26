---
title: "Association TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: d276a89f-6589-4785-9fb1-93e710aa0973
description: "The TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet association relates task baseline timephased data to a task and relates a task to a baseline timephased dataset."
---

# Association: TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet (ProjectData service)

The **TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet** association relates task baseline timephased data to a task and relates a task to a baseline timephased dataset. 
  
## Definition

```XML
<Association Name="TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet">
  <End Type="ReportingData.Task" Role="Task_BaselinesTimephasedDataSet" Multiplicity="0..1" />
  <End Type="ReportingData.TaskBaselineTimephasedData" Role="TaskBaselineTimephasedData_Task" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet** <br/> |Identifies the entity types and the navigation properties that form the two-way association for task baseline timephased data and tasks. In the first half of the name, **TaskBaselineTimephasedData** is the entity type and **Task** is the navigation property. In the second half of the name, **Task** is the entity type and **BaselinesTimephasedDataSet** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskBaselineTimephasedData_Task_Task_BaselinesTimephasedDataSet association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskBaselineTimephasedData_Task** <br/> |[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be many task baseline timephased data entities that correspond with a task.  <br/> |
|**Task_BaselinesTimephasedDataSet** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |There is one task entity that corresponds to a collection of task baseline timephased data.  <br/> |
   
## Remarks

One end of the association is the **TaskBaselineTimephasedData** entity, and the other end is the **Task** entity. The **TaskBaselineTimephasedData** entity type contains the **Task** navigation property, where the **FromRole** defines **TaskBaselineTimephasedData_Task** as the start of the association to get the task that is associated with a collection of task baseline timephased data. Similarly, the **Task** entity type contains the **BaselinesTimephasedDataSet** navigation property, where the **FromRole** defines **Task_BaselinesTimephasedDataSet** as the start of the association to get the baselines timephased dataset that is associated with a task. 
  
## See also

#### Reference

[EntityType element: Task](entitytype-task-projectdata-service.md)
  
[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md)

