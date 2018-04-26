---
title: "Association element ResourceConstraintScenario_ResourceScenarioProjects (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: fa44f9ea-fada-4a90-a474-0fb1c10393c8
description: "The ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario association relates a resource constraint scenario to resource scenario projects and relates resource scenario projects to a resource constraint scenario."
---

# Association element: ResourceConstraintScenario_ResourceScenarioProjects (ProjectServerData service)

The **ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario** association relates a resource constraint scenario to resource scenario projects and relates resource scenario projects to a resource constraint scenario. 
  
## Definition

```XML
<Association Name="ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario">
  <End Type="ReportingData.ResourceScenarioProject" Role="ResourceScenarioProject_ResourceConstraintScenario" Multiplicity="*" />
  <End Type="ReportingData.ResourceConstraintScenario" Role="ResourceConstraintScenario_ResourceScenarioProjects" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario** <br/> |Identifies the entity types and the navigation properties that form the two-way association for resource constraint scenarios and resource scenario projects. **ResourceConstraintScenario** is the entity type and **ResourceScenarioProjects** is the navigation property. In the second half of the name, **ResourceScenarioProject** is the entity type and **ResourceConstraintScenario** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceConstraintScenario_ResourceScenarioProjects** <br/> |[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md) <br/> |**0..1** <br/> |There is one resource constraint scenario entity that corresponds to a collection of resource scenario projects.  <br/> |
|**ResourceScenarioProject_ResourceConstraintScenario** <br/> |[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md) <br/> |**\*** <br/> |There can be many resource scenario project entities that correspond to a resource constraint scenarios.  <br/> |
   
## Remarks

One end of the association is the **ResourceConstraintScenario** entity, and the other end is the **ResourceScenarioProject** entity. The **ResourceConstraintScenario** entity type contains the **ResourceScenarioProjects** navigation property, where the **FromRole** defines **ResourceConstraintScenario_ResourceScenarioProjects** as the start of the association to get a collection of resource scenario projects that is associated with a resource constraint scenario. Similarly, the **ResourceScenarioProject** entity type contains the **ResourceConstraintScenario** navigation property, where the **FromRole** defines **ResourceScenarioProject_ResourceConstraintScenario** as the start of the association to get a resource constraint scenario that is associated with a collection of resource scenario projects. 
  
## See also

#### Reference

[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md)
  
[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md)

