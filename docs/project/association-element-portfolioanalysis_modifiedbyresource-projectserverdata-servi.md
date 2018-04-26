---
title: "Association element PortfolioAnalysis_ModifiedByResource (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: d8b731cd-7013-4b19-9acb-7fde18e62598
description: "The PortfolioAnalysis_ModifiedByResource relates portfolio analysis to the resource that did modifications."
---

# Association element: PortfolioAnalysis_ModifiedByResource (ProjectServerData service)

The **PortfolioAnalysis_ModifiedByResource** relates portfolio analysis to the resource that did modifications. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_ModifiedByResource">
  <End Type="ReportingData.Resource" Role="ModifiedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_ModifiedByResource** <br/> |Identifies the two entity types that form the **PortfolioAnalysis_ModifiedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_ModifiedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_ModifiedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**\*** <br/> |The collection of portfolio analyses in the reporting tables.  <br/> |
|**ModifiedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource that is referenced in the **PortfolioAnalysis_ModifiedByResource** association.  <br/> |
   
## Remarks

The **ModifiedByResource** navigation property in the **PortfolioAnalysis** entity uses the **PortfolioAnalysis_ModifiedByResource** association to query for a resource that performed modifications on portfolio analyses and is associated with a collection of portfolio analyses. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

