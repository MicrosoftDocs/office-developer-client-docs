---
title: "Association element ProjectBaseline_Project (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 2de2d0a1-0a05-4a3e-8ba5-79b18d0f0e8e
description: "The ProjectBaseline_Project association relates project baselines to a project."
---

# Association element: ProjectBaseline_Project (ProjectServerData service)

The **ProjectBaseline_Project** association relates project baselines to a project. 
  
## Definition

```XML
<Association Name="ProjectBaseline_Project">
  <End Type="ReportingData.ProjectBaseline" Role="ProjectBaseline" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ProjectBaseline_Project** <br/> |Identifies the two entity types that form the **ProjectBaseline_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child element

The **ProjectBaseline_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ProjectBaseline_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ProjectBaseline** <br/> |[EntityType element: ProjectBaseline](entitytype-projectbaseline-projectdata-service.md) <br/> |**\*** <br/> |The collection of project baseline in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **ProjectBaseline_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **ProjectBaseline** entity uses the **ProjectBaseline_Project** association to query for a project that is associated with a collection of project baselines. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: ProjectBaseline](entitytype-projectbaseline-projectdata-service.md)

