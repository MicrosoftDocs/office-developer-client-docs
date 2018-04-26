---
title: "Association PortfolioAnalysis_CreatedByResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 30d8a8a1-1efa-4ffe-9930-f23d4567da07
description: "The PortfolioAnalysis_CreatedByResource relates portfolio analyses to the creating resource."
---

# Association: PortfolioAnalysis_CreatedByResource (ProjectData service)

The **PortfolioAnalysis_CreatedByResource** relates portfolio analyses to the creating resource. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_CreatedByResource">
  <End Type="ReportingData.Resource" Role="CreatedByResource" Multiplicity="0..1" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_CreatedByResource** <br/> |Identifies the two entity types that form the **PortfolioAnalysis_CreatedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_CreatedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_CreatedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**\*** <br/> |The collection of portfolio analyses in the reporting tables.  <br/> |
|**CreatedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **PortfolioAnalysis_CreatedByResource** association.  <br/> |
   
## Remarks

The **CreatedByResource** navigation property in the **PortfolioAnalysis** entity uses the **PortfolioAnalysis_CreatedByResource** association to query for a resource that is associated with a collection of portfolio analyses. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

