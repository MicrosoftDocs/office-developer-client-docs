---
title: "Association CostScenarioProject_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 0aa119b5-f44b-4f5d-afec-11c2a345ae2a
description: "The CostScenarioProject_Project association relates cost scenario projects to a project."
---

# Association: CostScenarioProject_Project (ProjectData service)

The **CostScenarioProject_Project** association relates cost scenario projects to a project. 
  
## Definition

```XML
<Association Name="CostScenarioProject_Project">
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
  <End Type="ReportingData.CostScenarioProject" Role="CostScenarioProject" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostScenarioProject_Project** <br/> |Identifies the two entity types that form the **CostScenarioProject_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **CostScenarioProject_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the CostScenario_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostScenarioProjects** <br/> |[EntityType element: CostScenarioProjects](entityset-costscenarioprojects-projectdata-service.md) <br/> |**\*** <br/> |The collection of cost scenario projects in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entityset-projects-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is being referenced in the **CostScenarioProject_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property of the **CostScenario** entity type uses the **CostScenario _ Project** association to query for projects that are associated with a collection of cost scenario projects. 
  
## See also

#### Reference

[EntityType element: CostScenarioProjects](entityset-costscenarioprojects-projectdata-service.md)
  
[EntityType element: Project](entityset-projects-projectdata-service.md)

