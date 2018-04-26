---
title: "EntityType ResourceConstraintScenario (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 2708f1c3-fd31-4c8d-b67a-79c9fcc1bf4b
description: "Contains the properties that define the reporting data for a resource constraint scenario in the ProjectData service."
---

# EntityType: ResourceConstraintScenario (ProjectData service)

Contains the properties that define the reporting data for a resource constraint scenario in the **ProjectData** service. 
  
## Example

The following REST query uses the [ResourceConstraintScenarios](entityset-resourceconstraintscenarios-projectdata-service.md) entity set and the **ScenarioId** key to get the specified resource constraint scenario. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/ResourceConstraintScenarios
    ?$filter=ScenarioId eq guid'da4af49e-4b96-e211-a1ea-00155da01314'
```

## Definition

```XML
<EntityType Name="ResourceConstraintScenario">
  <Key>
    <PropertyRef Name="ScenarioId" />
  </Key>
  <Property Name="ScenarioId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="CreatedByResource" Relationship="ReportingData.ResourceConstraintScenario_CreatedByResource" ToRole="CreatedByResource" FromRole="ResourceConstraintScenario" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a resource constraint scenario and navigation properties of that resource constraint scenario. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as cost constraint scenarios, that are associated with a resource constraint scenario. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** element specifies the property that is the primary key for a resource constraint scenario query. **ScenarioId** is the scenario GUID. 
  
### Property elements

The following table lists the **Property** elements for the **ResourceConstraintScenario** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of ResourceConstraintScenario**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AllocationThreshold** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The percentage number between 0 and 100 that specifies the minimum threshold that is required for a resource to be allocated to a project.  <br/> |
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID for a portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis.  <br/> |
|**ConstraintType** <br/> |**Edm.Byte** <br/> |**false** <br/> |The type of restriction or constraint.  <br/> |
|**ConstraintValue** <br/> |**Edm.Decimal** <br/> |**false** <br/> |A value that indicates the limit of a constraint.  <br/> |
|**CostConstraintScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of a portfolio analysis cost constraint scenario.  <br/> |
|**CostConstraintScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a Portfolio Analysis cost constraint scenario.  <br/> |
|**CreatedByResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the resource that created a constraint.  <br/> |
|**CreatedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that created a constraint.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a constraint was created.  <br/> |
|**EnforceProjectDependencies** <br/> |**Edm.Boolean** <br/> |**false** <br/> |A flag that indicates whether project dependencies are enforced.  <br/> |
|**EnforceSchedulingConstraints** <br/> |**Edm.Boolean** <br/> |**false** <br/> |A flag that indicates whether scheduling constraints are enforced.  <br/> |
|**HiringType** <br/> |**Edm.Byte** <br/> |**false** <br/> |The internal or external hiring type.  <br/> |
|**ModifiedByResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the resource that last modified a constraint.  <br/> |
|**ModifiedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that last modified a constraint.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a constraint was last modified.  <br/> |
|**RateTable** <br/> |**Edm.Byte** <br/> |**false** <br/> |Specifies a rate table.  <br/> |
|**ScenarioDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of a Portfolio Analysis scenario.  <br/> |
|**ScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a Portfolio Analysis scenario.  <br/> |
|**ScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a Portfolio Analysis scenario.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **ResourceConstraintScenario** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Analysis** navigation property, the primary type is **PortfolioAnalysis**, and the secondary type is **ResourceConstraintScenario**. For this type of navigation, the **FromRole** is **PortfolioAnalysis_ResourceConstraintScenarios**, and the **ToRole** is **ResourceConstraintScenario_Analysis**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **CreatedByResource** navigation property relationship, **ResourceConstraintScenario** is the primary entity type and **CreatedByResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Analysis** <br/> |[PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis](association-element-portfolioanalysis_resourceconstraintscenarios-projectserverd.md) <br/> |Establishes navigation from a portfolio analysis to a collection of resource constraint scenarios and from a resource constraint scenario to an analysis.  <br/> |
|**CostConstraintScenario** <br/> |[CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario](association-costconstraintscenario_resourceconstraintscenarios_resourceconstrain.md) <br/> |Establishes navigation from a cost constraint scenario to a collection of resource constraint scenarios and from a resource constraint scenario to a cost constraint scenario.  <br/> |
|**CreatedByResource** <br/> |[ResourceConstraintScenario_CreatedByResource](association-resourceconstraintscenario_createdbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of resource constraint scenarios to the resource that created them.  <br/> |
|**ModifiedByResource** <br/> |[ResourceConstraintScenario_ModifiedByResource](association-resourceconstraintscenario_modifiedbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of resource constraint scenarios to the resource that modified them.  <br/> |
|**ResourceScenarioProjects** <br/> |[ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario](association-element-resourceconstraintscenario_resourcescenarioprojects-projects.md) <br/> |Establishes navigation from a resource constraint scenario to a collection of resource scenario projects and from a resource scenario project to a resource constraint scenario.  <br/> |
   
## See also

#### Reference

[ResourceConstraintScenarios](entityset-resourceconstraintscenarios-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

