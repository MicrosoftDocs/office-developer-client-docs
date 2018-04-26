---
title: "Association Deliverable_ParentTasks (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 18cb39e8-3c62-4ef0-9dca-3870bea8e2b8
description: "The Deliverable_ParentTasks association relates deliverables to parent tasks."
---

# Association: Deliverable_ParentTasks (ProjectData service)

The **Deliverable_ParentTasks** association relates deliverables to parent tasks. 
  
## Definition

```XML
<Association Name="Deliverable_ParentTasks">
  <End Type="ReportingData.Task" Role="ParentTasks" Multiplicity="*" />
  <End Type="ReportingData.Deliverable" Role="Deliverable" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Deliverable_ParentTasks** <br/> |Identifies the two entity types that form the **Deliverable_ParentTasks** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Deliverable_ParentTasks** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Deliverable_ParentTasks association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Deliverable** <br/> |[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |**\*** <br/> |The collection of deliverables in the reporting tables.  <br/> |
|**ParentTasks** <br/> |[EntityType element: Task](entitytype-task-projectdata-service.md) <br/> |**\*** <br/> |The collection of parent tasks in the reporting tables.  <br/> |
   
## Remarks

The **ParentTasks** navigation property in the **Deliverable** entity uses the **Deliverable_ParentTasks** association to query parent tasks that are associated with a collection of deliverables. 
  
## See also

#### Reference

[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md)
  
[EntityType element: Task](entitytype-task-projectdata-service.md)

