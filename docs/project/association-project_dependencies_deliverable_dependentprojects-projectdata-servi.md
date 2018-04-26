---
title: "Association Project_Dependencies_Deliverable_DependentProjects (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 7515b2e8-d9ee-4813-8644-948d8082d5a4
description: "The Project_Dependencies_Deliverable_DependentProjects association relates project to dependencies and relates deliverables to dependent projects."
---

# Association: Project_Dependencies_Deliverable_DependentProjects (ProjectData service)

The **Project_Dependencies_Deliverable_DependentProjects** association relates project to dependencies and relates deliverables to dependent projects. 
  
## Definition

```XML
<Association Name="Project_Dependencies_Deliverable_DependentProjects">
  <End Type="ReportingData.Deliverable" Role="Deliverable_DependentProjects" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Dependencies" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Dependencies_Deliverable_DependentProjects** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and deliverables. In the first half of the name, **Project** is the entity type and **Dependencies** is the navigation property. In the second half of the name, **Deliverable** is the entity type and **DependentProject** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Dependencies_Deliverable_DependentProjects** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Dependencies association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Dependencies** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**\*** <br/> |There can be many project entities that correspond to dependency entities.  <br/> |
|**Deliverable_DependentProjects** <br/> |[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |**\*** <br/> |There can be many deliverable entities that correspond to dependent projects.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Deliverable** entity. The **Project** entity type contains the **Dependencies** navigation property, where the **FromRole** defines **Project_Dependencies** as the start of the association to get the collection of dependencies for projects. Similarly, the **Deliverable** entity type contains the **DependentProjects** navigation property, where the **FromRole** defines **Deliverable_DependentProjects** as the start of the association to get the dependent projects that are associated with a collection of deliverables. 
  
## See also

#### Reference

[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

