---
title: "EntityType PortfolioAnalysis (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: f73b3c47-6c00-4481-b485-628b58480182
description: "Contains the properties that define the reporting data for a portfolio analysis in the ProjectData service."
---

# EntityType: PortfolioAnalysis (ProjectData service)

Contains the properties that define the reporting data for a portfolio analysis in the **ProjectData** service. 
  
## Example

The following REST query uses the [PortfolioAnalyses](entityset-portfolioanalyses-projectdata-service.md) entity set and the **DepartmentId** property to get portfolio analysis information for the specified department. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/PortfolioAnalyses
    ?$filter=DepartmentId eq guid'18b25c88-86a4-e111-9719-00155db24e18'
    &amp;$select=AnalysisId,AnalysisName,AnalysisDescription,HardConstraintCustomFieldName
```

## Definition

```XML
<EntityType Name="PortfolioAnalysis">
  <Key>
    <PropertyRef Name="AnalysisId" />
  </Key>
  <Property Name="AnalysisId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="CreatedByResource" Relationship="ReportingData.PortfolioAnalysis_CreatedByResource" ToRole="CreatedByResource" FromRole="PortfolioAnalysis" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a portfolio analysis and navigation properties of that portfolio analysis. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as analysis projects and prioritization, that are associated with a portfolio analysis. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** element specifies the property that is the primary key for a project query. **AnalysisId** is the portfolio analysis GUID. 
  
### Property elements

The following table lists the values of the **Property** elements for the **PortfolioAnalysis** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of PortfolioAnalysis**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AlternateProjectEndDateCustomFieldId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID for a custom field that contains an alternate end date and time for a portfolio analysis.  <br/> |
|**AlternateProjectEndDateCustomFieldName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a custom field that contains an alternate end date and time for a portfolio analysis.  <br/> |
|**AlternateProjectStartDateCustomFieldId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID for a custom field that contains an alternate start date for a portfolio analysis.  <br/> |
|**AlternateProjectStartDateCustomFieldName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a custom field that contains an alternate start date for a portfolio analysis.  <br/> |
|**AnalysisDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The text description for a portfolio analysis.  <br/> |
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID for a portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis.  <br/> |
|**AnalysisType** <br/> |**Edm.Int32** <br/> |**false** <br/> |The type of a portfolio analysis.  <br/> |
|**BookingType** <br/> |**Edm.Byte** <br/> |**false** <br/> |The assignment booking type (committed or proposed).  <br/> |
|**CreatedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that created a portfolio analysis.  <br/> |
|**CreatedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that created a portfolio analysis.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a portfolio analysis was created.  <br/> |
|**DepartmentId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a department in a portfolio analysis.  <br/> |
|**DepartmentName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a department in a portfolio analysis.  <br/> |
|**FilterResourcesByDepartment** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if resources are filtered by departments.  <br/> |
|**FilterResourcesByRBS** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if resources are filtered by Resource Breakdown Structure ( **RBS**).  <br/> |
|**FilterResourcesByRBSValueId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the **RBS** value that is used to filter resources.  <br/> |
|**FilterResourcesByRBSValueText** <br/> |**Edm.String** <br/> |**true** <br/> |The **RBS** text value that is used to filter resources.  <br/> |
|**ForcedInAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the lookup table that is used for forced-in aliasing.  <br/> |
|**ForcedInAliasLookupTableName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the lookup table that is used for forced-in aliasing.  <br/> |
|**ForcedOutAliasLookupTableId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the lookup table that is used for forced-out aliasing.  <br/> |
|**ForcedOutAliasLookupTableName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the lookup table that is used for forced-out aliasing.  <br/> |
|**HardConstraintCustomFieldId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the value that represents the sum of the primary constraint custom field values of projects selected in the optimizer.  <br/> |
|**HardConstraintCustomFieldName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the value that represents the sum of the primary constraint custom field values of projects selected in the optimizer.  <br/> |
|**ModifiedByResourceId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the resource that last updated a portfolio analysis.  <br/> |
|**ModifiedByResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource that last updated a portfolio analysis.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time when a portfolio analysis was modified.  <br/> |
|**PlanningHorizonEndDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The end of the date and time range that is considered in a portfolio analysis.  <br/> |
|**PlanningHorizonStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The beginning of the date and time range that is considered in a portfolio analysis.  <br/> |
|**PrioritizationId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID for a portfolio analysis prioritization.  <br/> |
|**PrioritizationName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis prioritization.  <br/> |
|**PrioritizationType** <br/> |**Edm.Int32** <br/> |**false** <br/> |The numerical value that represents the type of a portfolio analysis prioritization.  <br/> |
|**RoleCustomFieldId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of the custom field that is used to define a role.  <br/> |
|**RoleCustomFieldName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the custom field that is used to define a role.  <br/> |
|**TimeScale** <br/> |**Edm.Byte** <br/> |**false** <br/> |The scale of the timephased data.  <br/> |
|**UseAlternateProjectDatesForResourcePlans** <br/> |**Edm.Boolean** <br/> |**true** <br/> |**True** if alternate project dates are used for resource plans.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **PortfolioAnalysis** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **AnalysisProjects** navigation property, the primary type is **PortfolioAnalysis**, and the secondary type is **PortfolioAnalysisProject**. For this type of navigation, the **FromRole** is **PortfolioAnalysis_AnalysisProjects**, and the **ToRole** is **PortfolioAnalysisProject_Analysis**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **CreatedByResource** navigation property relationship, **PortfolioAnalysis** is the primary entity type and **CreatedByResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**AnalysisProjects** <br/> |[PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis](association-element-portfolioanalysis_analysisprojects-projectserverdata-service.md) <br/> |Establishes navigation from a portfolio analyses to a collection of portfolio analysis projects and from a portfolio analysis project to a portfolio analysis.  <br/> |
|**CostConstraintScenarios** <br/> |[PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis](association-portfolioanalysis_costconstraintscenarios_costconstraintscenario_ana.md) <br/> |Establishes navigation from a portfolio analyses to a collection of cost constraint scenarios and from a cost constraint scenario to a portfolio analysis.  <br/> |
|**CreatedByResource** <br/> |[PortfolioAnalysis_CreatedByResource](association-portfolioanalysis_createdbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of portfolio analyses to a resource.  <br/> |
|**ModifiedByResource** <br/> |[PortfolioAnalysis_ModifiedByResource](association-element-portfolioanalysis_modifiedbyresource-projectserverdata-servi.md) <br/> |Establishes navigation from a collection of portfolio analyses to a resource.  <br/> |
|**Prioritization** <br/> |[PortfolioAnalysis_Prioritization](association-element-portfolioanalysis_prioritization-projectserverdata-service.md) <br/> |Establishes navigation from a collection of portfolio analyses to a prioritization.  <br/> |
|**ResourceConstraintScenarios** <br/> |[PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis](association-element-portfolioanalysis_resourceconstraintscenarios-projectserverd.md) <br/> |Establishes navigation from a portfolio analyses to a collection of resource constraint scenarios and from a resource constraint scenario to a portfolio analysis.  <br/> |
   
## See also

#### Reference

[PortfolioAnalyses](entityset-portfolioanalyses-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

