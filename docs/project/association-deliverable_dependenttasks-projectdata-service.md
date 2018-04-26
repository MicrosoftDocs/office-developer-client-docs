---
title: "Association Deliverable_DependentTasks (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 65dbed5f-b0f8-473c-a253-96a4c030680b
description: "The Deliverable_DependentTasks association relates the deliverable to its dependent tasks."
---

# Association: Deliverable_DependentTasks (ProjectData service)

The **Deliverable_DependentTasks** association relates the deliverable to its dependent tasks. 
  
## Definition

```XML
<Association Name="Deliverable_DependentTasks">
  <End Type="ReportingData.Task" Role="DependentTasks" Multiplicity="*" />
  <End Type="ReportingData.Deliverable" Role="Deliverable" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Deliverable_DependentTasks** <br/> |Identifies the two entity types that form the **Deliverable_DependentTasks** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Deliverable_DependentTasks** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**. Attributes of the End elements for the Deliverable_DependentTasks association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Deliverable** <br/> |[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |**\*** <br/> |The collection of deliverables in the reporting tables.  <br/> |
|**DependentTasks** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**\*** <br/> |The collection of dependent tasks in the reporting tables.  <br/> |
   
## Remarks

The **DependentTasks** navigation property in the **Deliverable** entity uses the **Deliverable_DependentTasks** association to query for dependent tasks that are associated with deliverables. 
  
## See also

#### Reference

[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

