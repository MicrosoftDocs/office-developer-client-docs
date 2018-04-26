---
title: "EntityType CostConstraintScenario (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 9a4c9974-b2d8-45a9-9cb4-8f1a76f2bbfb
description: "Contains the properties that define the reporting data for a cost constraint scenario in the ProjectData service."
---

# EntityType: CostConstraintScenario (ProjectData service)

Contains the properties that define the reporting data for a cost constraint scenario in the **ProjectData** service. 
  
## Example

The following REST query uses the [CostConstraintScenarios](entityset-costconstraintscenarios-projectdata-service.md) entity set and the **ScenarioId** key to get the specified cost constraint scenario. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/CostConstraintScenarios
    ?$filter=ScenarioId eq guid'd0bd9ee7-4b96-e211-9faf-00155da22112'
```

## Definition

```XML
<EntityType Name="CostConstraintScenario">
  <Key>
    <PropertyRef Name="ScenarioId" />
  </Key>
  <Property Name="ScenarioId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="CreatedByResource" Relationship="ReportingData.CostConstraintScenario_CreatedByResource" ToRole="CreatedByResource" FromRole="CostConstraintScenario" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a cost constraint scenario and navigation properties of that cost constraint scenario. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as analyses and resource constraint scenarios, that are associated with a cost constraint scenario. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** element specifies the property that is the primary key for a query for a cost constraint scenario. **ScenarioId** is the scenario GUID. 
  
### Property elements

The following table lists the values of the **Property** elements for the **CostConstraintScenario** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of CostConstraintScenario**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the portfolio analysis.  <br/> |
|**CreatedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that created the cost constraint scenario.  <br/> |
|**CreatedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that created the cost constraint scenario.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the cost constraint scenario was created.  <br/> |
|**ModifiedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that last changed the cost constraint scenario.  <br/> |
|**ModifiedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that last changed the cost constraint scenario.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the cost constraint scenario was modified.  <br/> |
|**ScenarioDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the cost constraint scenario.  <br/> |
|**ScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the cost constraint scenario.  <br/> |
|**ScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the cost constraint scenario.  <br/> |
|**SelectedProjectsCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total cost of the projects that are selected in the cost constraint scenario.  <br/> |
|**SelectedProjectsPriority** <br/> |**Edm.Double** <br/> |**true** <br/> |The total priority of the projects that are selected in the cost constraint scenario.  <br/> |
|**UnselectedProjectsCost** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The total cost of the projects that are not selected in the cost constraint scenario.  <br/> |
|**UnselectedProjectsPriority** <br/> |**Edm.Double** <br/> |**true** <br/> |The total priority of the projects that are not selected in the cost constraint scenario.  <br/> |
|**UseDependencies** <br/> |**Edm.Boolean** <br/> |**false** <br/> |Indicates whether to use dependency links in a project.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **CostConstraintScenario** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Analysis** navigation property, the primary type is **PortfolioAnalysis**, and the secondary type is **CostConstraintScenario**. For this type of navigation, the **FromRole** is **PortfolioAnalysis_CostConstraintScenarios**, and the **ToRole** is **CostConstraintScenario_Analysis**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **CreatedByResource** navigation property relationship, **CostConstraintScenario** is the primary entity type and **CreatedByResource** is the secondary entity type 
  
**Attribute values of the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Analysis** <br/> |[PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis](association-portfolioanalysis_costconstraintscenarios_costconstraintscenario_ana.md) <br/> |Establishes navigation from a portfolio analysis to a collection of cost constraint scenarios and from a cost constraint scenarios to a portfolio analysis.  <br/> |
|**CostScenarioProjects** <br/> |[CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario](association-costconstraintscenario_costscenarioprojects_costscenarioproject_cost.md) <br/> |Establishes navigation from a cost constraint scenario to a collection of cost scenario projects and from a cost scenario project to a cost constraint scenario.  <br/> |
|**CreatedByResource** <br/> |[CostConstraintScenario_CreatedByResource](association-costconstraintscenario_createdbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of cost constraint scenarios to the resource that created the scenario.  <br/> |
|**ModifiedByResource** <br/> |[CostConstraintScenario_ModifiedByResource](association-costconstraintscenario_modifiedbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of cost constraint scenarios to the resource that modified the scenario.  <br/> |
|**ResourceConstraintScenarios** <br/> |[CostConstraintScenario_ResourceConstraintScenarios_ResourceConstraintScenario_CostConstraintScenario](association-costconstraintscenario_resourceconstraintscenarios_resourceconstrain.md) <br/> |Establishes navigation from a cost constraint scenario to a collection of resource constraint scenarios and from a resource constraint scenarios to a cost constraint scenario.  <br/> |
   
## See also

#### Reference

[CostConstraintScenarios](entityset-costconstraintscenarios-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

