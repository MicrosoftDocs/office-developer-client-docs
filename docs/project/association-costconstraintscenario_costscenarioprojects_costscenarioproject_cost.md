---
title: "Association CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 3badeda8-23b0-405a-94e8-e9341df8952e
description: "The CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario association relates a cost constraint scenario to cost scenario projects and relates cost scenario projects to a cost constraint scenario."
---

# Association: CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario (ProjectData service)

The **CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario** association relates a cost constraint scenario to cost scenario projects and relates cost scenario projects to a cost constraint scenario. 
  
## Definition

```XML
<Association Name="CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario">
  <End Type="ReportingData.CostScenarioProject" Role="CostScenarioProject_CostConstraintScenario" Multiplicity="*" />
  <End Type="ReportingData.CostConstraintScenario" Role="CostConstraintScenario_CostScenarioProjects" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario** <br/> |Identifies the entity types and the navigation properties that form the two-way association for cost constrainst scenarios and cost scenario projects.In the first half of the name, **CostConstraintScenario** is the entity type and **CostScenarioProjects** is the navigation property. In the second half of the name, **CostScenarioProject** is the entity type and **CostConstraintScenario** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostConstraintScenario_CostScenarioProjects** <br/> |[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md) <br/> |**0..1** <br/> |There is one cost constraint scenario that corresponds to a collection of cost scenario projects.  <br/> |
|**CostScenarioProject_CostConstraintScenario** <br/> |[EntityType element: CostScenarioProject](entitytype-costscenarioproject-projectdata-service.md) <br/> |**\*** <br/> |There can be many cost scenario projects that correspond with a cost constraint scenario.  <br/> |
   
## Remarks

One end of the association is the **CostConstraintScenario** entity, and the other end is the **CostScenarioProject** entity. The **CostConstraintScenario** entity type contains the **CostScenarioProjects** navigation property, where the **FromRole** defines **CostConstraintScenario_CostScenarioProjects** as the start of the association to get the cost scenario projects that are associated with a cost constraint scenario. Similarly, the **CostScenarioProject** entity type contains the **CostConstraintScenario** navigation property, where the **FromRole** defines **CostScenarioProject_CostConstraintScenario** as the start of the association to get the cost constraint scenario that is associated with a collection of cost scenario projects. 
  
## See also

#### Reference

[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md)
  
[EntityType element: CostScenarioProject](entitytype-costscenarioproject-projectdata-service.md)

