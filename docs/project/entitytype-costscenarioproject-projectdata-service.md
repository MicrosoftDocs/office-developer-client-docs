---
title: "EntityType CostScenarioProject (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 182e0ae3-0592-482f-865f-68d51027e2d7
description: "Contains the properties that define the reporting data for a cost scenario project in the ProjectData service."
---

# EntityType: CostScenarioProject (ProjectData service)

Contains the properties that define the reporting data for a cost scenario project in the **ProjectData** service. 
  
## Example

The following REST query uses the [CostScenarioProjects](entityset-costscenarioprojects-projectdata-service.md) entity set and the **ScenarioId** key to get the specified cost scenario projects. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/CostScenarioProjects
    ?$filter=ScenarioId eq guid'd0bd9ee7-4b96-e211-9faf-00155da22112'
```

## Definition

```XML
<EntityType Name="CostScenarioProject">
  <Key>
    <PropertyRef Name="ScenarioId" />
    <PropertyRef Name="ProjectId" />
  </Key>
  <Property Name="ScenarioId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.CostScenarioProject_Project" ToRole="Project" FromRole="CostScenarioProject" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a cost scenario project and navigation properties of that cost scenario project. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such analyses or projects, that are associated with a cost scenario project. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a cost scenario project query. **ScenarioId** is the scenario GUID and the **ProjectId** is the GUID of the project. 
  
### Property elements

The following table lists the values of the **Property** elements for the **CostScenarioProject** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of CostScenarioProject**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AbsolutePriority** <br/> |**Edm.Double** <br/> |**false** <br/> |The non-normalized priority ranking for a project within the portfolio analysis.  <br/> |
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the portfolio analysis.  <br/> |
|**ForceAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the lookup table structure value that is used in the analysis.  <br/> |
|**ForceAliasLookupTableName** <br/> |**Edm.String** <br/> |**true** <br/> |The text value of the lookup table structure that is used in the analysis.  <br/> |
|**ForceStatus** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that specifies whether project status is a forced decision.  <br/> |
|**HardConstraintValue** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The value that represents the sum of the primary constraint custom field values for projects that are selected in the optimizer.  <br/> |
|**Priority** <br/> |**Edm.Double** <br/> |**false** <br/> |The priority level of the cost constraint project.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**ScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a portfolio analysis scenario.  <br/> |
|**ScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis scenario.  <br/> |
|**Status** <br/> |**Edm.Byte** <br/> |**false** <br/> |The status of the cost scenario project.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **CostScenarioProject** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **CostConstraintScenario** navigation property, the primary type is **CostConstraintScenario**, and the secondary type is **CostScenarioProject**. For this type of navigation, the **FromRole** is **CostConstraintScenario_CostScenarioProjects**, and the **ToRole** is **CostScenarioProject_CostConstraintScenario**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **CostScenarioProject** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Analysis** <br/> |[CostScenarioProject_Analysis](association-costscenarioproject_analysis-projectdata-service.md) <br/> |Establishes navigation from a collection of cost scenario projects to an analysis.  <br/> |
|**CostConstraintScenario** <br/> |[CostConstraintScenario_CostScenarioProjects_CostScenarioProject_CostConstraintScenario](association-costconstraintscenario_costscenarioprojects_costscenarioproject_cost.md) <br/> |Establishes navigation from a cost constraint scenario to a collection of cost scenario projects and from a cost scenario project to a cost constraint scenario.  <br/> |
|**Project** <br/> |[CostScenarioProject_Project](association-costscenarioproject_project-projectdata-service.md) <br/> |Establishes navigation from a collection of cost scenario projects to a project.  <br/> |
   
## See also

#### Reference

[CostScenarioProjects](entityset-costscenarioprojects-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

