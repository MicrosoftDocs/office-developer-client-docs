---
title: "EntitySet Deliverables (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 3d97c166-8e38-4bb9-b8b7-31afa0a391d3
description: "Specifies the collection of deliverables in the ReportingData schema."
---

# EntitySet: Deliverables (ProjectData service)

Specifies the collection of deliverables in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Deliverables" EntityType="ReportingData.Deliverable" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Deliverables** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Deliverable** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

