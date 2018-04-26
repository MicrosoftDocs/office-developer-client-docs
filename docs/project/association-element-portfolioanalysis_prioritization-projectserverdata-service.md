---
title: "Association element PortfolioAnalysis_Prioritization (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 3d1149b6-2eb4-4775-b0c5-08595682b92f
description: "The PortfolioAnalysis_Prioritization association relates portfolio analyses to a prioritization."
---

# Association element: PortfolioAnalysis_Prioritization (ProjectServerData service)

The **PortfolioAnalysis_Prioritization** association relates portfolio analyses to a prioritization. 
  
## Definition

```XML
<Association Name="PortfolioAnalysis_Prioritization">
  <End Type="ReportingData.Prioritization" Role="Prioritization" Multiplicity="0..1" />
  <End Type="ReportingData.PortfolioAnalysis" Role="PortfolioAnalysis" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PortfolioAnalysis_Prioritization** <br/> |Identifies the two entity types that form the **PortfolioAnalysis_Prioritization** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PortfolioAnalysis_Prioritization** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PortfolioAnalysis_Prioritization association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PortfolioAnalysis** <br/> |[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md) <br/> |**\*** <br/> |The collection of portfolio analyses in the reporting tables.  <br/> |
|**Prioritization** <br/> |[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md) <br/> |**0..1** <br/> |The prioritization object that is referenced in the **PortfolioAnalysis_Prioritization** association.  <br/> |
   
## Remarks

The **Prioritization** navigation property in the **PortfolioAnalysis** entity uses the **PortfolioAnalysis_Prioritization** association to query for a prioritization that is associated with a collection of portfolio analysis prioritizations. 
  
## See also

#### Reference

[EntityType element: PortfolioAnalysis](entitytype-portfolioanalysis-projectdata-service.md)
  
[EntityType element: Prioritization](entitytype-prioritization-projectdata-service.md)

