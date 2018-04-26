---
title: "EntitySet TimesheetLines (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e78ff662-ef36-4b20-8220-f341ac44f95c
description: "Specifies the collection of timesheet lines in the ReportingData schema."
---

# EntitySet: TimesheetLines (ProjectData service)

Specifies the collection of timesheet lines in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="TimesheetLines" EntityType="ReportingData.TimesheetLine" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLines** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.TimesheetLine** <br/> |The type of entity.  <br/> |
   
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
  

