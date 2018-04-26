---
title: "EntitySet TaskBaselines (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: e732e1d4-5e6d-40ee-9869-9b2994dae14a
description: "Specifies the collection of task baselines in the ReportingData schema."
---

# EntitySet: TaskBaselines (ProjectData service)

Specifies the collection of task baselines in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="TaskBaselines" EntityType="ReportingData.TaskBaseline" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaselines** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.TaskBaseline** <br/> |The type of entity.  <br/> |
   
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
  

