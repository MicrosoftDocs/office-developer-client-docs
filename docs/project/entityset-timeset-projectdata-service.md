---
title: "EntitySet TimeSet (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 614f54f3-e428-469a-ac91-7319ce120b85
description: "Specifies the collection of timeset data in the ReportingData schema."
---

# EntitySet: TimeSet (ProjectData service)

Specifies the collection of timeset data in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="TimeSet" EntityType="ReportingData.Time" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimeSet** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Time** <br/> |The type of entity.  <br/> |
   
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
  

