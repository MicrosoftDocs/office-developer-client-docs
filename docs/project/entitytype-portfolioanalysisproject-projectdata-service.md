---
title: "EntityType PortfolioAnalysisProject (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 20aed496-9f0f-4f2f-8a45-37f83d0b720a
description: "Contains the properties that define the reporting data for a portfolio analysis project in the ProjectData service."
---

# EntityType: PortfolioAnalysisProject (ProjectData service)

Contains the properties that define the reporting data for a portfolio analysis project in the **ProjectData** service. 
  
## Example

The following REST query uses the [PortfolioAnalysisProjects](entityset-portfolioanalysisprojects-projectdata-service.md) entity set and the **AnalysisId** key to get the specified portfolio analysis projects. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/PortfolioAnalysisProjects
    ?$filter=AnalysisId eq guid'71ae9370-68b3-e111-bdc2-00155d35d31e'
```

## Definition

```XML
<EntityType Name="PortfolioAnalysisProject">
  <Key>
    <PropertyRef Name="AnalysisId" />
    <PropertyRef Name="ProjectId" />
  </Key>
  <Property Name="AnalysisId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Analysis" Relationship="ReportingData.PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis" ToRole="PortfolioAnalysis_AnalysisProjects" FromRole="PortfolioAnalysisProject_Analysis" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a portfolio analysis project and navigation properties of that portfolio analysis project. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as analysis id and analysis name, that are associated with a prioritization driver. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a query for a portfolio analysis project. **ProjectId** is the project GUID and **AnalysisId** identifies the portfolio analysis. 
  
### Property elements

The following table lists the values of the **Property** elements for the **PortfolioAnalysisProject** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of PortfolioAnalysisProject**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AbsolutePriority** <br/> |**Edm.Double** <br/> |**false** <br/> |The non-normalized priority ranking for a project within the Portfolio Analysis.  <br/> |
|**AnalysisId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID for a portfolio analysis.  <br/> |
|**AnalysisName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a portfolio analysis.  <br/> |
|**Duration** <br/> |**Edm.Decimal** <br/> |**true** <br/> |The duration of a portfolio analysis.  <br/> |
|**FinishNoLaterThan** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The last date and time by which a portfolio analysis is complete.  <br/> |
|**Locked** <br/> |**Edm.Byte** <br/> |**true** <br/> |The project locked status code.  <br/> |
|**OriginalEndDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The original end date and time of a portfolio analysis.  <br/> |
|**OriginalStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The original start date and time of a portfolio analysis.  <br/> |
|**Priority** <br/> |**Edm.Double** <br/> |**false** <br/> |The priority ranking value for a portfolio analysis.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project in the portfolio analysis.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project in the portfolio analysis.  <br/> |
|**StartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The start date and time for a project in the portfolio analysis.  <br/> |
|**StartNoEarlierThan** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The earliest start date and time for a project in the portfolio analysis.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **PortfolioAnalysisProject** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Analysis** navigation property, the primary type is **PortfolioAnalysis**, and the secondary type is **PortfolioAnalysisProject**. For this type of navigation, the **FromRole** is **PortfolioAnalysis_AnalysisProjects**, and the **ToRole** is **PortfolioAnalysisProject_Analysis**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **PortfolioAnalysisProject** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Analysis** <br/> |[PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis](association-element-portfolioanalysis_analysisprojects-projectserverdata-service.md) <br/> |Establishes navigation from a portfolio analysis to a collection of analysis projects and from a portfolio analysis project to an analysis.  <br/> |
|**Project** <br/> |[PortfolioAnalysisProject_Project](association-portfolioanalysisproject_project-projectdata-service.md) <br/> |Establishes navigation from a collection of portfolio analysis projects to a project.  <br/> |
   
## See also

#### Reference

[PortfolioAnalysisProjects](entityset-portfolioanalysisprojects-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

