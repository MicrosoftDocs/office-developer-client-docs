---
title: "Association PortfolioAnalysisProject_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: c937d352-25f5-40b1-8c7b-ebc83d91a32f
description: "The PortfolioAnalysisProject_Project association relates portfolio analysis projects to a project."
---

# Association: PortfolioAnalysisProject_Project (ProjectData service)

The **PortfolioAnalysisProject_Project** association relates portfolio analysis projects to a project. 
  
## Definition

```XML
<Association Name="PortfolioAnalysisProject_Project">
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
  <End Type="ReportingData.PortfolioAnalysisProject" Role="PortfolioAnalysisProject" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysisProject_Project** <br/> |Identifies the two entity types that form the **PortfolioAnalysisProject_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysisProject_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysisProject_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysisProject** <br/> |[EntityType element: PortfolioAnalysisProject](entitytype-portfolioanalysisproject-projectdata-service.md) <br/> |**\*** <br/> |The portfolio analysis projects in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **PortfolioAnalysisProject_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **PortfolioAnalysisProject** entity uses the **PortfolioAnalysisProject_Project** association to query for a project that is associated with a collection of portfolio analysis projects. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysisProject](entitytype-portfolioanalysisproject-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

