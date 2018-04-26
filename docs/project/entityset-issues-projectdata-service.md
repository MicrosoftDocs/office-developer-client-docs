---
title: "EntitySet Issues (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 00d9fcc1-247d-4781-9ff4-0dbb788d9bdb
description: "Specifies the collection of issues in the ReportingData schema."
---

# EntitySet: Issues (ProjectData service)

Specifies the collection of issues in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Issues" EntityType="ReportingData.Issue" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Issues** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Issue** <br/> |The type of entity.  <br/> |
   
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
  

