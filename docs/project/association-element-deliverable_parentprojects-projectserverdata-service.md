---
title: "Association element Deliverable_ParentProjects (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f0de64bc-d5cc-46a9-8e13-3d273bb817ba
description: "The Deliverable_ParentProjects association relates the deliverable to its parent projects."
---

# Association element: Deliverable_ParentProjects (ProjectServerData service)

The **Deliverable_ParentProjects** association relates the deliverable to its parent projects. 
  
## Definition

```XML
<Association Name="Deliverable_ParentProjects">
  <End Type="ReportingData.Project" Role="ParentProjects" Multiplicity="*" />
  <End Type="ReportingData.Deliverable" Role="Deliverable" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Deliverable_ParentProjects** <br/> |Identifies the two entity types that form the **Deliverable_ParentProjects** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Deliverable_ParentProjects** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Deliverable_ParentProjects association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Deliverable** <br/> |[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |**\*** <br/> |The collection of deliverables in the reporting tables.  <br/> |
|**ParentProjects** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**\*** <br/> |The collection of parent projects in the reporting tables.  <br/> |
   
## Remarks

The **ParentProjects** navigation property in the **Deliverable** entity uses the **Deliverable_ParentProjects** association to query parent projects that are associated with a collection of deliverables. 
  
## See also

#### Reference

[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

