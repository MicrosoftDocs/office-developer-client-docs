---
title: "EntitySet CostScenarioProjects (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 901cae08-55a1-4ae3-b2c0-cef25480e3d1
description: "Specifies the collection of cost scenario projects for project portfolio analysis in the ReportingData schema."
---

# EntitySet: CostScenarioProjects (ProjectData service)

Specifies the collection of cost scenario projects for project portfolio analysis in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="CostScenarioProjects" EntityType="ReportingData.CostScenarioProject" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**CostScenarioProjects** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.CostScenarioProject** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Remarks

The **CostScenarioProjects** entity set has a default maximum page limit of 200 cost scenario projects in one query. For information about how to query for more than 200 cost scenario projects, and how to get and set the page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

