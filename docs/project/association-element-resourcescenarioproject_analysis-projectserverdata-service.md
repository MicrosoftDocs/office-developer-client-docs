---
title: "Association element ResourceScenarioProject_Analysis (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6c5baa7e-4175-4157-b79f-5e252c5a4b5e
description: "The ResourceScenarioProject_Analysis association relates resource scenario projects to an analysis."
---

# Association element: ResourceScenarioProject_Analysis (ProjectServerData service)

The **ResourceScenarioProject_Analysis** association relates resource scenario projects to an analysis. 
  
## Definition

```XML
<Association Name="ResourceScenarioProject_Analysis">
  <End Type="ReportingData.ResourceScenarioProject" Role="ResourceScenarioProject" Multiplicity="*" />
  <End Type="ReportingData.PortfolioAnalysis" Role="Analysis" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ResourceScenarioProject_Analysis** <br/> |Identifies the two entity types that form the **ResourceScenarioProject_Analysis** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **ResourceScenarioProject_Analysis** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the ResourceScenarioProject_Analysis association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**ResourceScenarioProject** <br/> |[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md) <br/> |**\*** <br/> |The collection of resource scenario projects in the reporting tables.  <br/> |
|**Analysis** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**0..1** <br/> |The analysis object that is referenced in the **ResourceScenarioProject_Analysis** association.  <br/> |
   
## Remarks

The **Analysis** navigation property in the **ResourceScenarioProject** entity uses the **ResourceScenarioProject_Analysis** association to query for an analysis that is associated with a collection of resource scenario projects. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: ResourceScenarioProject](entitytype-resourcescenarioproject-projectdata-service.md)

