---
title: "Association CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 367f7155-2747-46ca-9e24-bfa8f685ed6c
description: "The CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario association relates a cost constraint scenario to the resource constraint scenarios that it contains and relates resource constraint scenarios to a cost constraint scenario."
---

# Association: CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario (ProjectData service)

The **CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario** association relates a cost constraint scenario to the resource constraint scenarios that it contains and relates resource constraint scenarios to a cost constraint scenario. 
  
## Definition

```XML
<Association Name="CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario">
  <End Type="ReportingData.ResourceConstraintScenario" Role="ResourceConstraintScenario_CostConstraintScenario" Multiplicity="*" />
  <End Type="ReportingData.CostConstraintScenario" Role="CostConstraintScenario_ResourceConstraintScenarios" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario** <br/> |Identifies the entity types and the navigation properties that form the two-way association for cost constraint scenarios and resource constraint scenarios. In the first half of the name, **CostConstraintScenario** is the entity type and **ResourceConstraintScenarios** is the navigation property. In the second half of the name, **ResourceConstraintScenario** is the entity type and **CostConstraintScenario** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostConstraintScenario_ResourceConstraintScenarios** <br/> |[EntityType element: CostConstraintScenarios](entitytype-costconstraintscenario-projectdata-service.md) <br/> |**0..1** <br/> |There can be one cost constraint scenario entity that corresponds to a collection of resource constraint scenarios.  <br/> |
|**ResourceConstraintScenario_CostConstraintScenario** <br/> |[EntityType element: ResourceConstraintScenarios](entitytype-resourceconstraintscenario-projectdata-service.md) <br/> |**\*** <br/> |There can be many resource constraint scenario entities that correspond with a cost constraint scenario.  <br/> |
   
## Remarks

One end of the association is the **CostConstraintScenario** entity, and the other end is the **ResourceConstraintScenario** entity. The **CostConstraintScenario** entity type contains the **ResourceConstraintScenarios** navigation property, where the **FromRole** defines **CostConstraintScenario_ResourceConstraintScenarios** as the start of the association to get the collection of resource constraint scenarios that are associated with a cost constraint scenario. Similarly, the **ResourceConstraintScenario** entity type contains the **CostConstraintScenario** navigation property, where the **FromRole** defines **ResourceConstraintScenario_CostConstraintScenario** as the start of the association to get the cost constraint scenario that is associated with a collection of resource constraint scenarios. 
  
## See also

#### Reference

[EntityType element: CostConstraintScenarios](entitytype-costconstraintscenario-projectdata-service.md)
  
[EntityType element: ResourceConstraintScenarios](entitytype-resourceconstraintscenario-projectdata-service.md)

