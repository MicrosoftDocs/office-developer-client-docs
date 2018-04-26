---
title: "EntitySet BusinessDriverDepartments (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 6a77ad6c-be8f-45ac-9b41-b41822b38393
description: "Specifies the collection of business driver departments for project portfolio analysis in the ReportingData schema."
---

# EntitySet: BusinessDriverDepartments (ProjectData service)

Specifies the collection of business driver departments for project portfolio analysis in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="BusinessDriverDepartments" EntityType="ReportingData.BusinessDriverDepartment" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**BusinessDriverDepartments** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.BusinessDriverDepartment** <br/> |The type of entity.  <br/> |
   
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
  

