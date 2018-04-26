---
title: "EntitySet PrioritizationDrivers (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 7aae98fd-a0a3-49b7-a3a8-fe013d0a7fc4
description: "Specifies the collection of project prioritization drivers for portfolio analyses in the ReportingData schema."
---

# EntitySet: PrioritizationDrivers (ProjectData service)

Specifies the collection of project prioritization drivers for portfolio analyses in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="PrioritizationDrivers" EntityType="ReportingData.PrioritizationDriver" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PrioritizationDrivers** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.PrioritizationDriver** <br/> |The type of entity.  <br/> |
   
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
  

