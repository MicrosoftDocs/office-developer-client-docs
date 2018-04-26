---
title: "Association ResourceScenarioProject_CostConstraintScenario (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 0cb7c6cc-84df-49ff-a144-c2495136e9e0
description: "The ResourceScenarioProject_CostConstraintScenario association relates resource scenario projects to a cost constraint scenario."
---

# Association: ResourceScenarioProject_CostConstraintScenario (ProjectData service)

The **ResourceScenarioProject_CostConstraintScenario** association relates resource scenario projects to a cost constraint scenario. 
  
## Definition

```XML
<Association Name="ResourceScenarioProject_CostConstraintScenario">
  <End Type="ReportingData.ResourceScenarioProject" Role="ResourceScenarioProject" Multiplicity="*" />
  <End Type="ReportingData.CostConstraintScenario" Role="CostConstraintScenario" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceScenarioProject_CostConstraintScenario** <br/> |Identifies the two entity types that form the **ResourceScenarioProject_CostConstraintScenario** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceScenarioProject_CostConstraintScenario** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceScenarioProject_CostConstraintScenario association**

|**Role**|**Type**|**Multplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceScenarioProject** <br/> |[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md) <br/> |**\*** <br/> |The collection of resource scenario projects in the reporting tables.  <br/> |
|**CostConstraintScenario** <br/> |[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md) <br/> |**0..1** <br/> |The cost constraint scenario object in the **ResourceScenarioProject_CostConstraintScenario** association.  <br/> |
   
## Remarks

The **CostConstraintScenario** navigation property in the **ResourceScenarioProject** entity uses the **ResourceScenarioProject_CostConstraintScenario** association to query for a cost constraint scenario that is associated with a collection of resource scenario projects. 
  
## See also

#### Reference

[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md)
  
[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md)

