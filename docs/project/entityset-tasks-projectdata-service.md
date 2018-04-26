---
title: "EntitySet Tasks (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: ac124fc4-5b3b-4835-8b4a-ba5783b22d6d
description: "Specifies the collection of tasks in the ReportingData schema."
---

# EntitySet: Tasks (ProjectData service)

Specifies the collection of tasks in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Tasks" EntityType="ReportingData.Task" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Tasks** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Task** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Example

The following statement uses LINQ query syntax to retrieve **Task** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Tasks** entity set can then be accessed as  `context.Tasks`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from t in Tasks
    where (t.TaskIndex > 0)
    orderby t.ProjectName, t.TaskIndex
    select new
    {
        Project = t.ProjectName,
        Task = t.TaskName,
        TaskWork = t.TaskWork,
        TaskCost = t.TaskCost,
        TaskDuration = t.TaskDuration,
        TaskDurationVariance = t.TaskDurationVariance,
        TaskCostVariance = t.TaskCostVariance
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Tasks
    .Where(t => (t.TaskIndex > (Int32)0))
    .OrderBy(t => t.ProjectName)
    .ThenBy(t => t.TaskIndex)
    .Select(t => new
    {
        Project = t.ProjectName,
        Task = t.TaskName,
        TaskWork = t.TaskWork,
        TaskCost = t.TaskCost,
        TaskDuration = t.TaskDuration,
        TaskDurationVariance = t.TaskDurationVariance,
        TaskCostVariance = t.TaskCostVariance
    });
```

Either statement creates the following REST URL (all on one line).
  
```HTML
http://ServerName/pwa/_vti_bin/client.svc/ProjectServerData/Tasks()?
     $filter=TaskIndex gt 0&amp;
     $orderby=ProjectName,TaskIndex&amp;$select=ProjectName,TaskName,TaskWork,
     TaskCost,TaskDuration,TaskDurationVariance,TaskCostVariance
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**Task**|**TaskWork**|**TaskCost**|**TaskDuration**|**TaskDurationVariance**|**TaskCostVariance**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |T1  <br/> |24.0 hrs  <br/> |$404.00  <br/> |24.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectA  <br/> |T2  <br/> |8.0 hrs  <br/> |$156.00  <br/> |8.0 hrs  <br/> |-16.0 hrs  <br/> |-$272.00  <br/> |
|ProjectA  <br/> |T3  <br/> |32.0 hrs  <br/> |$564.00  <br/> |32.0 hrs  <br/> |8.0 hrs  <br/> |$136.00  <br/> |
|ProjectB  <br/> |T1  <br/> |48.0 hrs  <br/> |$836.00  <br/> |48.0 hrs  <br/> |16.0 hrs  <br/> |$272.00  <br/> |
|ProjectB  <br/> |T2  <br/> |24.0 hrs  <br/> |$428.00  <br/> |24.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectB  <br/> |T3  <br/> |40.0 hrs  <br/> |$740.00  <br/> |40.0 hrs  <br/> |0.0 hrs  <br/> |$0.00  <br/> |
|ProjectB  <br/> |T4  <br/> |8.0 hrs  <br/> |$168.00  <br/> |8.0 hrs  <br/> |-8.0 hrs  <br/> |-$168.00  <br/> |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

