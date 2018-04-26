---
title: "EntitySet ProjectBaselines (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: ab4d5d06-4a82-4bd1-9d2f-98dfb08295a7
description: "Specifies the collection of project baselines in the ReportingData schema."
---

# EntitySet: ProjectBaselines (ProjectData service)

Specifies the collection of project baselines in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="ProjectBaselines" EntityType="ReportingData.ProjectBaseline" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**ProjectBaselines** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.ProjectBaseline** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Example

The following statement uses LINQ query syntax to retrieve **ProjectBaseline** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **ProjectBaselines** entity set can then be accessed as  `context.ProjectBaselines`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
    var query =
    from p in ProjectBaselines
    select new
    {
        ProjectName = p.ProjectName,
        StartDate = p.ProjectBaselineStartDate,
        EndDate = p.ProjectBaselineFinishDate,
        ProjectBaselineWork = p.ProjectBaselineWork,
        ProjectBaselineCost = p.ProjectBaselineCost
    };

```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
    var query = ProjectBaselines
    .Select( p => new
    {
        ProjectName = p.ProjectName,
        StartDate = p.ProjectBaselineStartDate,
        EndDate = p.ProjectBaselineFinishDate,
        ProjectBaselineWork = p.ProjectBaselineWork,
        ProjectBaselineCost = p.ProjectBaselineCost
    });

```

Either statement creates the following REST URL (all on one line).
  
```HTML
http://ServerName/pwa/_vti_bin/client.svc/ProjectServerData/ProjectBaselines()?
$select=ProjectName,ProjectBaselineStartDate,ProjectBaselineFinishDate,ProjectBaselineWork,ProjectBaselineCost

```

All three of the sample queries get the same data.
  
**Sample results of the ProjectBaseline query**

|**ProjectName**|**StartDate**|**EndDate**|**ProjectBaselineWork**|**ProjectBaselineCost**|
|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |3/26/2012 8:00:00 AM  <br/> |3/30/2012 5:00:00 PM  <br/> |144.0 hrs  <br/> |$2380.00  <br/> |
|ProjectB  <br/> |3/12/2012 8:00:00 AM  <br/> |3/16/2012 5:00:00 PM  <br/> |87.5 hrs  <br/> |$1835.90  <br/> |
|ProjectC  <br/> |3/12/2012 8:00:00 AM  <br/> |3/17/2012 5:00:00 PM  <br/> |112.0 hrs  <br/> |$1872.00  <br/> |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

