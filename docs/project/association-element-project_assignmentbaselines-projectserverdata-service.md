---
title: "Association element Project_AssignmentBaselines (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 03c9e2fe-eafe-4630-baeb-5510fffb0201
description: "The Project_AssignmentBaselines_AssignmentBaseline_Project association relates a project to the assignment baselines that it contains and relates assignment baselines to a project."
---

# Association element: Project_AssignmentBaselines (ProjectServerData service)

The **Project_AssignmentBaselines_AssignmentBaseline_Project** association relates a project to the assignment baselines that it contains and relates assignment baselines to a project. 
  
## Definition

```XML
<Association Name="Project_AssignmentBaselines_AssignmentBaseline_Project">
  <End Type="ReportingData.AssignmentBaseline" Role="AssignmentBaseline_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_AssignmentBaselines" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_AssignmentBaselines_AssignmentBaseline_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and assignment baselines. In the first half of the name, **Project** is the entity type and **AssignmentBaselines** is the navigation property. In the second half of the name, **AssignmentBaseline** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_AssignmentBaselines_AssignmentBaseline_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_AssignmentBaselines_AssignmentBaseline_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_AssignmentBaselines** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of assignment baselines.  <br/> |
|**AssignmentBaseline_Project** <br/> |[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md) <br/> |**\*** <br/> |There can be many assignment baseline entities in a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **AssignmentBaseline** entity. The **Project** entity type contains the **AssignmentBaselines** navigation property, where the **FromRole** defines **Project_AssignmentBaselines** as the start of the association to get the collection of assignment baselines that are associated with a project. Similarly, the **AssignmentBaseline** entity type contains the **Project** navigation property, where the **FromRole** defines **AssignmentBaseline_Project** as the start of the association to get the project that is associated with a collection of assignment baselines. 
  
## See also

#### Reference

[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

