---
title: "Association element Project_Deliverables (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 50b5fb74-2fc5-49bd-bbdd-2109732c67bf
description: "The Project_Deliverables_Deliverable_Project association relates a project to the deliverables that it contains and relates deliverables to projects."
---

# Association element: Project_Deliverables (ProjectServerData service)

The **Project_Deliverables_Deliverable_Project** association relates a project to the deliverables that it contains and relates deliverables to projects. 
  
## Definition

```XML
<Association Name="Project_Deliverables_Deliverable_Project">
  <End Type="ReportingData.Deliverable" Role="Deliverable_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Deliverables" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Deliverables_Deliverable_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and deliverables. In the first half of the name, **Project** is the entity type and **Deliverables** is the navigation property. In the second half of the name, **Deliverable** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Deliverables_Deliverable_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Deliverables_Deliverable_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Deliverables** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There can one project that corresponds to a collection of deliverables.  <br/> |
|**Deliverable_Project** <br/> |[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md) <br/> |**\*** <br/> |There can be many deliverables that correspond to a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Deliverable** entity. The **Project** entity type contains the **Deliverables** navigation property, where the **FromRole** defines **Project_Deliverables** as the start of the association to get the collection of deliverables that are associated with a project. Similarly, the **Deliverable** entity type contains the **Project** navigation property, where the **FromRole** defines **Deliverable_Project** as the start of the association to get the project that is associated with a collection of deliverables. 
  
## See also

#### Reference

[EntityType element: Deliverable](entitytype-deliverable-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

