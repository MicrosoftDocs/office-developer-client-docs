---
title: "EntitySet Risks (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: a8b0ffb7-4701-47b2-979b-6e5078d81f53
description: "Specifies the collection of risks in the ReportingData schema."
---

# EntitySet: Risks (ProjectData service)

Specifies the collection of risks in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Risks" EntityType="ReportingData.Risk" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Resources** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Resource** <br/> |The type of entity.  <br/> |
   
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
  

