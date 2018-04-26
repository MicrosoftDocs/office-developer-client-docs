---
title: "Association element PortfolioAnalysis_AnalysisProjects (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 787cd979-0dd6-4dcd-9781-4e69f6344ff6
description: "The PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis association relates a portfolio analysis to the analysis projects that it contains and relates portfolio analysis projects to an analysis."
---

# Association element: PortfolioAnalysis_AnalysisProjects (ProjectServerData service)

The **PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis** association relates a portfolio analysis to the analysis projects that it contains and relates portfolio analysis projects to an analysis. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis">
  <End Type="ReportingData.PortfolioAnalysisProject" Role="PortfolioAnalysisProject_Analysis" Multiplicity="*" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis_AnalysisProjects" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis** <br/> |Identifies the entity types and the navigation properties that form the two-way association for portfolio analyses and portfolio analysis projects. In the first half of the name, **PortfolioAnalysis** is the entity type and **AnalysisProjects** is the navigation property. In the second half of the name, **PortfolioAnalysisProject** is the entity type and **Analysis** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_AnalysisProjects_PortfolioAnalysisProject_Analysis association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis_AnalysisProjects** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**0..1** <br/> |There is one portfolio analysis entity that corresponds to a collection of analysis projects.  <br/> |
|**PortfolioAnalysisProject_Analysis** <br/> |[EntityType element: PortfolioAnalysisProject](entitytype-portfolioanalysisproject-projectdata-service.md) <br/> |**\*** <br/> |There can be many portfolio analysis project entities that correspond with an analysis.  <br/> |
   
## Remarks

One end of the association is the **PortfolioAnalysis** entity, and the other end is the **PortfolioAnalysisProject** entity. The **PortfolioAnalysis** entity type contains the **AnalysisProjects** navigation property, where the **FromRole** defines **PortfolioAnalysis_AnalysisProjects** as the start of the association to get the collection of analysis project that are associated with a portfolio analysis. Similarly, the **PortfolioAnalysisProject** entity type contains the **Analysis** navigation property, where the **FromRole** defines **PortfolioAnalysisProject_Analysis** as the start of the association to get the analysis that is associated with a collection of portfolio analysis projects. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: PortfolioAnalysisProject](entitytype-portfolioanalysisproject-projectdata-service.md)

