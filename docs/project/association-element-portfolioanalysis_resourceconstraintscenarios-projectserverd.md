---
title: "Association element PortfolioAnalysis_ResourceConstraintScenarios (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6ac8d1ff-8c29-481d-97f1-2d4e207bf89e
description: "The PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis association relates portfolio analyses to resource constraint scenarios."
---

# Association element: PortfolioAnalysis_ResourceConstraintScenarios (ProjectServerData service)

The **PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis** association relates portfolio analyses to resource constraint scenarios. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis">
  <End Type="ReportingData.ResourceConstraintScenario" Role="ResourceConstraintScenario_Analysis" Multiplicity="*" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis_ResourceConstraintScenarios" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis** <br/> |Identifies the entity types and the navigation properties that form the two-way association for a portfolio analysis and resource constraint scenarios. In the first half of the name, **PortfolioAnalysis** is the entity type and **ResourceConstraintScenarios** is the navigation property. In the second half of the name, **ResourceConstraintScenario** is the entity type and **Analysis** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_ResourceConstraintScenarios_ResourceConstraintScenario_Analysis association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis_ResourceConstraintScenarios** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**0..1** <br/> |There is one portfolio analysis entity that corresponds to a collection resource constraint scenarios.  <br/> |
|**ResourceConstraintScenario_Analysis** <br/> |[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md) <br/> |**\*** <br/> |There can be many resource constraint entities that correspond with an analysis.  <br/> |
   
## Remarks

One end of the association is the **PortfolioAnalysis** entity, and the other end is the **ResourceConstraintScenario** entity. The **PortfolioAnalysis** entity type contains the **ResourceConstraintScenarios** navigation property, where the **FromRole** defines **PortfolioAnalysis_ResourceConstraintScenarios** as the start of the association to get the collection of resource constraint scenarios in a portfolio analysis. Similarly, the **ResourceConstraintScenario** entity type contains the **Analysis** navigation property, where the **FromRole** defines **ResourceConstraintScenario_Analysis** as the start of the association to get the portfolio analysis that is associated with a collection of resource constraint scenarios. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: ResourceConstraintScenario](entitytype-resourceconstraintscenario-projectdata-service.md)

