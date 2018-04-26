---
title: "Association element AssignmentTimephasedData_Task (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b64f6073-5e44-4cf6-8f71-1c7a95153863
description: "The AssignmentTimephasedData_Task association relates assignment timephased data to a task."
---

# Association element: AssignmentTimephasedData_Task (ProjectServerData service)

The **AssignmentTimephasedData_Task** association relates assignment timephased data to a task. 
  
## Definition

```XML
<Association Name="AssignmentTimephasedData_Task">
  <End Type="ReportingData.Task" Role="Task" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentTimephasedData" Role="AssignmentTimephasedData" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentTimephasedData_Task** <br/> |Identifies the two entity types that form the **AssignmentTimephasedData_Task** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentTimephasedData_Task** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentTimephasedData_Task association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentTimephasedData** <br/> |[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of assignment timephased data in the reporting tables.  <br/> |
|**Task** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**0..1** <br/> |The task object that is being referenced in the **Assignment_Task** association.  <br/> |
   
## Remarks

The **Task** navigation property in the **AssignmentTimephasedData** entity uses the **AssignmentTimephasedData_Task** association to query for a task that is associated with a collection of assignment timephased data. 
  
## See also

#### Reference

[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

