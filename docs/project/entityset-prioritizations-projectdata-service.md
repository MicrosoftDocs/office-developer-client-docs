---
title: "EntitySet Prioritizations (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: c0d97f85-1f7b-4032-9123-9d5943774cfb
description: "Specifies the collection of project prioritizations for portfolio analyses in the ReportingData schema."
---

# EntitySet: Prioritizations (ProjectData service)

Specifies the collection of project prioritizations for portfolio analyses in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Prioritizations" EntityType="ReportingData.Prioritization" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Prioritizations** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Prioritization** <br/> |The type of entity.  <br/> |
   
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
  

