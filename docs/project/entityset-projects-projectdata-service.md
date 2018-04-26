---
title: "EntitySet Projects (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: fad2b25b-2de7-4b2f-95f4-9cd6d00d29f2
description: "Specifies the collection of projects in the ReportingData schema."
---

# EntitySet: Projects (ProjectData service)

Specifies the collection of projects in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Projects" EntityType="ReportingData.Project" />
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Projects** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Project** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Example

```cs
var query =
    from p in Projects
    where p.ProjectStartDate > new DateTime(2012, 1, 1)
    orderby p.ProjectName
    select new
    {
        Project = p.ProjectName,
        StartDate = p.ProjectStartDate,
        FinishDate = p.ProjectFinishDate,
        ProjectCost = p.ProjectCost
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Projects
    .Where(p => (p.ProjectStartDate > (DateTime?)(new DateTime(2012, 1, 1))))
    .OrderBy(p => p.ProjectName)
    .Select(p => new
    {
        Project = p.ProjectName,
        StartDate = p.ProjectStartDate,
        FinishDate = p.ProjectFinishDate,
        ProjectCost = p.ProjectCost
    });
```

Either statement creates the following REST URL (all on one line).
  
```HTML
http://ServerName/pwa/_vti_bin/client.svc/ProjectServerData/Projects()?
    $filter=ProjectStartDate gt datetime'2012-01-01T00:00:00'&amp;
    $orderby=ProjectName&amp;
    $select=ProjectName,ProjectStartDate,ProjectFinishDate,ProjectCost
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**StartDate**|**FinishDate**|**ProjectCost**|
|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |3/1/2012 8:00:00 AM  <br/> |3/15/2012 5:00:00 PM  <br/> |$1124.00  <br/> |
|ProjectB  <br/> |3/1/2012 8:00:00 AM  <br/> |3/24/2012 5:00:00 PM  <br/> |$2171.00  <br/> |
|ProjectC  <br/> |3/1/2012 8:00:00 AM  <br/> |3/17/2012 5:00:00 PM  <br/> |$1968.00  <br/> |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)

