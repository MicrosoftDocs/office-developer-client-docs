---
title: "Association PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b7a3fd4f-21b2-43d3-9da6-ea45132db305
description: "The PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis association relates a portfolio analysis to the cost constraint scenarios that it contains and relates a collection of cost constraint scenarios to its portfolio analysis."
---

# Association: PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis (ProjectData service)

The **PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis** association relates a portfolio analysis to the cost constraint scenarios that it contains and relates a collection of cost constraint scenarios to its portfolio analysis. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis">
  <End Type="ReportingData.CostConstraintScenario" Role="CostConstraintScenario_Analysis" Multiplicity="*" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis_CostConstraintScenarios" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis** <br/> |Identifies the entity types and the navigation properties that form the two-way association for portfolio analyses and cost constraint scenarios. In the first half of the name, **PortfolioAnalysis** is the entity type and **CostConstraintScenarios** is the navigation property. In the second half of the name, **CostConstraintScenario** is the entity type and **Analysis** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_CostConstraintScenarios_CostConstraintScenario_Analysis association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis_CostConstraintScenarios** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**0..1** <br/> |There is one portfolio analysis entity that corresponds to a collection of cost constraint scenarios.  <br/> |
|**CostConstraintScenario_Analysis** <br/> |[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md) <br/> |**\*** <br/> |There can be many cost constraint scenarios entities in an analysis.  <br/> |
   
## Remarks

One end of the association is the **PortfolioAnalysis** entity, and the other end is the **CostConstraintScenario** entity. The **PortfolioAnalysis** entity type contains the **CostConstraintScenarios** navigation property, where the **FromRole** defines **PortfolioAnalysis_CostConstraintScenarios** as the start of the association to get the collection of cost constraint scenarios that are associated with a portfolio analysis. Similarly, the **CostConstraintScenario** entity type contains the **Analysis** navigation property, where the **FromRole** defines **CostConstraintScenario_Analysis** as the start of the association to get the portfolio analysis that is associated with a collection of cost constraint scenarios. 
  
## See also

#### Reference

[EntityType element: CostConstraintScenario](entitytype-costconstraintscenario-projectdata-service.md)
  
[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)

