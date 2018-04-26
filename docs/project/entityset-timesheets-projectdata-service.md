---
title: "EntitySet Timesheets (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 0cc93f37-6bf3-491e-8d8c-11594a11e4dc
description: "Specifies the collection of timesheets in the ReportingData schema."
---

# EntitySet: Timesheets (ProjectData service)

Specifies the collection of timesheets in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Timesheets" EntityType="ReportingData.Timesheet" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Timesheets** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Timesheet** <br/> |The type of entity.  <br/> |
   
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
  

