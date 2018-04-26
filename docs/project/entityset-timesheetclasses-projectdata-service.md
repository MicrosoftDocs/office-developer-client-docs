---
title: "EntitySet TimesheetClasses (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: f9060235-d2a8-41f7-8b93-017b844ca787
description: "Specifies the collection of timesheet classes in the ReportingData schema."
---

# EntitySet: TimesheetClasses (ProjectData service)

Specifies the collection of timesheet classes in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="TimesheetClasses" EntityType="ReportingData.TimesheetClass" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetClasses** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.TimesheetClass** <br/> |The type of entity.  <br/> |
   
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
  

