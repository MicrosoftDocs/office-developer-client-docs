---
title: "EntityType ResourceScenarioProject (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6f12da5a-10ee-4980-8881-ad6978bf9ced
description: "Contains the properties that define the reporting data for a resource scenario project in the ProjectData service."
---

# EntityType: ResourceScenarioProject (ProjectData service)

Contains the properties that define the reporting data for a resource scenario project in the **ProjectData** service. 
  
## Example

The following REST query uses the [ResourceScenarioProjects](entityset-resourcescenarioprojects-projectdata-service.md) entity set and the **ScenarioId** key to get the specified resource scenario. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/ResourceScenarioProjects
    ?$filter=ScenarioId eq guid'da4af49e-4b96-e211-a1ea-00155da01314'
```

## Definition

```XML
<EntityType Name="ResourceScenarioProject">
  <Key>
    <PropertyRef Name="ScenarioId" />
    <PropertyRef Name="ProjectId" />
  </Key>
  <Property Name="ScenarioId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.ResourceScenarioProject_Project" ToRole="Project" FromRole="ResourceScenarioProject" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a resource scenario project and navigation properties of that resource scenario project. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as analyses and resource constraint scenarios, that are associated with a resource scenario project. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a resource scenario project query. **ScenarioId** is the GUID of the scenario and **ProjectId** is the project GUID. 
  
### Property elements

The following table lists the **Property** elements for the **ResourceScenarioProject** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of ResourceScenarioProject**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AbsolutePriority** <br/> |**Edm.Double** <br/> |**false** <br/> |The non-normalized priority ranking for a project within a portfolio analysis.  <br/> |
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID for a portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis.  <br/> |
|**CostConstraintScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of a portfolio analysis cost constraint scenario.  <br/> |
|**CostConstraintScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis cost constraint scenario.  <br/> |
|**ForceAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the lookup table structure value that is used in the analysis.  <br/> |
|**ForceAliasLookupTableName** <br/> |**Edm.String** <br/> |**true** <br/> |The text value of the lookup table structure that is used in the analysis.  <br/> |
|**ForceStatus** <br/> |**Edm.Byte** <br/> |**false** <br/> |A value that indicates whether project status is a forced decision.  <br/> |
|**HardConstraintValue** <br/> |**Edm.Decimal** <br/> |**false** <br/> |A value that represents the sum of the primary constraint custom field values of projects that are selected in the optimizer.  <br/> |
|**NewStartDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The new start date and time of a project.  <br/> |
|**Priority** <br/> |**Edm.Double** <br/> |**false** <br/> |The priority level of a resource scenario project.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**ResourceCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost of a resource on a project.  <br/> |
|**ResourceWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The amount of work that is performed by a resource on a project.  <br/> |
|**ScenarioId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a portfolio analysis scenario.  <br/> |
|**ScenarioName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis scenario.  <br/> |
|**Status** <br/> |**Edm.Byte** <br/> |**false** <br/> |The status of a resource scenario project.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **ResourceScenarioProject** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **ResourceConstraintScenario** navigation property, the primary type is **ResourceConstraintScenario**, and the secondary type is **ResourceScenarioProject**. For this type of navigation, the **FromRole** is **ResourceConstraintScenario_ResourceScenarioProjects**, and the **ToRole** is **ResourceScenarioProject_ResourceConstraintScenari**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Analysis** navigation property relationship, **ResourceScenarioProject** is the primary entity type and **Analysis** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Analysis** <br/> |[ResourceScenarioProject_Analysis](association-element-resourcescenarioproject_analysis-projectserverdata-service.md) <br/> |Establishes navigation from a collection of resource scenario projects to an analysis.  <br/> |
|**CostConstraintScenario** <br/> |[ResourceScenarioProject_CostConstraintScenario](association-resourcescenarioproject_costconstraintscenario-projectdata-service.md) <br/> |Establishes navigation from a collection of resource scenario projects to a cost constraint scenario.  <br/> |
|**Project** <br/> |[ResourceScenarioProject_Project](association-element-resourcescenarioproject_project-projectserverdata-service.md) <br/> |Establishes navigation from a collection of resource scenario projects to a project.  <br/> |
|**ResourceConstraintScenario** <br/> |[ResourceConstraintScenario_ResourceScenarioProjects_ResourceScenarioProject_ResourceConstraintScenario](association-element-resourceconstraintscenario_resourcescenarioprojects-projects.md) <br/> |Establishes navigation from a resource constraint scenario to a collection of resource scenario projects and from a resource scenario project to a resource constraint scenario.  <br/> |
   
## See also

#### Reference

[ResourceScenarioProjects](entityset-resourcescenarioprojects-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

