---
title: "Association CostScenarioProject_Analysis (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 7e32b926-bbfa-42f8-9098-aa716c53da49
description: "The CostScenarioProject_Analysis association relates cost scenarios projects to a portfolio analysis."
---

# Association: CostScenarioProject_Analysis (ProjectData service)

The **CostScenarioProject_Analysis** association relates cost scenarios projects to a portfolio analysis. 
  
## Definition

```XML
<Association Name="CostScenarioProject_Analysis">
  <End Type="ReportingData.PortfolioAnalysis" Role="Analysis" Multiplicity="0..1" />
  <End Type="ReportingData.CostScenarioProject" Role="CostScenarioProject" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostScenarioProject_Analysis** <br/> |Identifies the two entity types that form the **CostScenarioProject_Analysis** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **CostScenarioProject_Analysis** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the CostScenarioProject_Analysis association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostScenarioProject** <br/> |[EntityType element: CostScenarioProject](entitytype-costscenarioproject-projectdata-service.md) <br/> |**\*** <br/> |The collection of cost scenario projects in the reporting tables.  <br/> |
|**Analysis** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**0..1** <br/> |The analysis object that is being referenced in the **CostScenarioProject_Analysis** association.  <br/> |
   
## Remarks

The **Analysis** navigation property of the **CostScenarioProject** entity type uses the **CostScenarioProject_Analysis** association to query for an analysis that is associated with a collection of cost scenario projects. 
  
## See also

#### Reference

[EntityType element: CostScenarioProject](entitytype-costscenarioproject-projectdata-service.md)
  
[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)

