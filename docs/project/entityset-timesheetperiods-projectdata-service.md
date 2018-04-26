---
title: "EntitySet TimesheetPeriods (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 861e4734-9a92-4b86-b906-f25c73a3ba1d
description: "Specifies the collection of timesheet periods in the ReportingData schema."
---

# EntitySet: TimesheetPeriods (ProjectData service)

Specifies the collection of timesheet periods in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="TimesheetPeriods" EntityType="ReportingData.TimesheetPeriod" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetPeriods** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.TimesheetPeriod** <br/> |The type of entity.  <br/> |
   
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
  

